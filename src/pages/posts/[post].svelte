<script>
  import { params } from '@sveltech/routify'
  $: id = $params.post
  import data from './posts.js'
</script>

<div class="mdc-typography--headline1">{data[id - 1].title}</div>
<div class="mdc-typography--headline2">{data[id - 1].desc}</div>

<div class="container-for-text">
<div class="mdc-typography--body2">{data[id - 1].content}</div>
</div>

<style>
div.mdc-typography--headline1 {
    text-align: center;
}
div.mdc-typography--headline2 {
    text-align: center;
    font-style: italic;
}
div.mdc-typography--body2 {
    font-size: 1.5em;
}
.container-for-text {
    width: 60%;
    margin: auto;
    border: solid 3px;
    padding: 50px;
    border-radius: 15px;
}
</style>