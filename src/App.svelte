<script>
  import { Router } from '@sveltech/routify'
  import { routes } from '@sveltech/routify/tmp/routes'
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/icon?family=Material+Icons" />
</svelte:head>
<Router {routes} />
