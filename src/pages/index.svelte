<script>
  import { Modal } from '@components'
  import Button, { Label, Icon } from '@smui/button'
  let showModal = false
</script>

<style lang="scss">
  header-text {
    div.mdc-typography--headline1 {
      margin: auto;
      text-align: center;
    }
    div.mdc-typography--subtitle2 {
      margin: auto;
      text-align: center;
    }
  }
</style>

<header-text>
  <div class="mdc-typography--headline1">
    Welcome to the template!
  </div>
  <div class="mdc-typography--subtitle2">
    Original by
    <a href="https://github.com/pankod/svelte-boilerplate">pankod</a>
  </div>
</header-text>
