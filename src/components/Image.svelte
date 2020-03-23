<script>
  export let src;
  export let alt;
  export let height = "50px";
  export let width = "50px";
  export let type;
</script>

<style>
  .profile-img {
    border-radius: 25px;
    float: left;
    margin: 10px;
  }
  .content-img {
    border-radius: 20px;
    border: 1px #ccd6dc;
  }
</style>

{#if type === 'content'}
  <img class="content-img" {src} {alt} {height} {width} />
{:else}
  <img class="profile-img" {src} {alt} {height} {width} />
{/if}
