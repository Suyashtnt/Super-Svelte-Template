<script>
  import { createEventDispatcher } from 'svelte'

  export let text = ''

  const dispatch = createEventDispatcher()

  const onClick = event => {
    dispatch('click', event)
  }
</script>

<style src="./style.scss">

</style>

<button class="button" on:click={onClick}>{text}</button>
