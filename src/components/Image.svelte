<script>
  export let src;
  export let alt;
  export let height = "50px";
  export let width = "50px";
  export let type;
  export let className = "";
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
  .cover-img {
    border: none;
    border-radius: 0;
  }
</style>

{#if type === 'content'}
  <img class="content-img" style={className} {src} {alt} {height} {width} />
{:else if type === 'cover'}
  <img class="cover-img" style={className} {src} {alt} {height} {width} />
{:else if (type = 'avatar')}
  <img class="profile-img " style={className} {src} {alt} {height} {width} />
{/if}
