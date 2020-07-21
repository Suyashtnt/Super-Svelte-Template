<script>
  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar'
  import IconButton from '@smui/icon-button'

  import { goto, url } from '@sveltech/routify'
  import { onMount } from 'svelte'

  // Show mobile icon and display menu
  let showMobileMenu = false

  // List of navigation items
  const navItems = [
    { label: 'Posts', href: $url('../posts') },
    { label: 'Item 2', href: $url('../posts/1') },
  ]

  const amount = navItems.length / 2
  const baseURL = '/'
  console.log(amount)

  // Mobile menu click event handler
  const handleMobileIconClick = () =>
    (showMobileMenu = !showMobileMenu)

  // Media match query handler
  const mediaQueryHandler = e => {
    // Reset mobile state
    if (!e.matches) {
      showMobileMenu = false
    }
  }

  // Attach media query listener on mount hook
  onMount(() => {
    const mediaListener = window.matchMedia('(max-width: 767px)')

    mediaListener.addListener(mediaQueryHandler)
  })
</script>

<style lang="scss">
  nav {
    background-color: rgba(0, 0, 0, 0.8);
    font-family: 'Helvetica Neue', 'Helvetica', 'Arial', sans-serif;
    height: 45px;
  }

  .inner {
    max-width: 980px;
    margin: auto;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    height: 100%;
  }

  .mobile-icon {
    width: 25px;
    height: 14px;
    position: relative;
    cursor: pointer;

    &:after,
    &:before {
      content: '';
      position: absolute;
      width: 100%;
      height: 2px;
      background-color: #fff;
      transition: all 0.4s;
      transform-origin: center;
    }
  }

  .middle-line {
    content: '';
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
    transition: all 0.4s;
    transform-origin: center;
  }

  .mobile-icon:before,
  .middle-line {
    top: 0;
  }

  .mobile-icon:after,
  .middle-line {
    bottom: 0;
  }

  .mobile-icon {
    &:before {
      width: 66%;
    }

    &:after {
      width: 33%;
    }
  }

  .middle-line {
    margin: auto;
  }

  .mobile-icon {
    &:hover {
      &:before,
      &:after {
        width: 100%;
      }
    }

    &.active {
      &:before,
      &:after,
      .middle-line {
        width: 100%;
      }

      &:before,
      &:after {
        top: 50%;
        transform: rotate(-45deg);
      }

      .middle-line {
        transform: rotate(45deg);
      }
    }
  }

  .navbar-list {
    display: none;
    width: 100%;
    justify-content: space-between;
    margin: 0;
    padding: 0 40px;

    &.mobile {
      background-color: rgba(0, 0, 0, 0.8);
      position: fixed;
      display: block;
      height: calc(100% - 45px);
      bottom: 0;
      left: 0;
    }

    li {
      list-style-type: none;
      position: relative;

      &:before {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 1px;
        background-color: #424245;
      }
    }

    a {
      color: #fff;
      text-decoration: none;
      display: flex;
      height: 45px;
      align-items: center;
      padding: 0 10px;
      font-size: 13px;
    }
  }

  @media only screen and (min-width: 767px) {
    .mobile-icon {
      display: none;
    }

    .navbar-list {
      display: flex;
      padding: 0;

      a {
        display: inline-flex;
      }
    }
  }

  :global(*) {
    vertical-align: baseline;
    font-weight: inherit;
    font-family: inherit;
    font-style: inherit;
    font-size: 100%;
    border: 0 none;
    outline: 0;
    padding: 0;
    margin: 0;
  }

  .title {
    font-size: 3rem;
    color: #fff;
    font-style: bold;
    font-family: 'Sora', sans-serif;
    padding: 0 10px;
    display: inline-flex;
  }
</style>

<svelte:head>
  <link
    href="https://fonts.googleapis.com/css2?family=Sora:wght@600&display=swap"
    rel="stylesheet" />
</svelte:head>

<!-- to change what is in the nav bar look at the script-->
<nav>
  <div class="inner">
    <div
      on:click={handleMobileIconClick}
      class={`mobile-icon${showMobileMenu ? ' active' : ''}`}>
      <div class="middle-line" />
    </div>
    <ul class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>
      {#each navItems as item, index}
        {#if index === amount}
          <li class="title">
            <a href={baseURL}>[amazing title here]</a>
          </li>
        {/if}
        <li>
          <a href={item.href}>{item.label}</a>
        </li>
      {/each}
    </ul>
  </div>
</nav>

<slot />
