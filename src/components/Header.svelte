<script>
  import FaTwitter from "svelte-icons/fa/FaTwitter.svelte";
</script>

<style>
  .header {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  .inner {
    justify-content: space-between;
    flex-direction: row;
    display: flex;
    border: 1px solid #e6ecf0;
    width: 600px;
    font-weight: bold;
    padding-top: 1em;
    padding-bottom: 0.75em;
    margin-bottom: 2em;
    background-color: white;
    position: fixed;
    top: 0;
  }
  h3 {
    color: grey;
    text-align: left;
    margin-left: 10px;
  }
  .icon {
    color: #1da1f2;
    height: 25px;
    width: 25px;
    margin-right: 1em;
  }
</style>

<div class="header">
  <div class="inner">
    <h3>Home</h3>
    <div class="icon">
      <FaTwitter />
    </div>
  </div>
</div>
