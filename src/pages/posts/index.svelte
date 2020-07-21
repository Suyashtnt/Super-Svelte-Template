<script>
  import { url, goto } from '@sveltech/routify'
  import data from './posts.js'
  import List, {
    Group,
    Item,
    Graphic,
    Meta,
    Label,
    Separator,
    Subheader,
    Text,
    PrimaryText,
    SecondaryText,
  } from '@smui/list'

  function gotoPage(id) {
       $goto(`/posts/${id}`)
  }
</script>

<a href="#/" class="item">
</a>

<List>
  {#each data as post}
    <Item class="item" on:SMUI:action={() => gotoPage(post.id)}>
      <Text>
        <PrimaryText>{post.title}</PrimaryText>
        <SecondaryText>{post.desc}</SecondaryText>
      </Text>
      <Meta class="material-icons">info</Meta>
    </Item>
  {/each}
</List>

<style lang="scss">
* :global(.item)     {
     padding: 0px 10px; 
}
</style>