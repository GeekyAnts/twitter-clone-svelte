<script>
  import Image from "./Image.svelte";

  let userFeed;
  let placeholder = "What's happening?";
</script>

<style>
  .header {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  .inner {
    width: 600px;
    flex-direction: row;
    display: inline-flex;
  }
  input {
    margin: 10px;
    flex: 1;
    outline: 0;
    border: none;
  }
  input::placeholder {
    font-size: 20px;
    color: #9197a3;
    font-family: Arial, Helvetica, sans-serif;
  }
  button {
    border-radius: 25px;
    background-color: rgb(23, 191, 99);
    padding: 10px;
    color: white;
    width: 20%;
    margin: 0.25em;
    align-self: flex-end;
  }
  hr {
    background-color: #e6ecf0;
    height: 10px;
    width: 100%;
    border: none;
  }
</style>

<div class="header">
  <div class="inner">
    <Image src="user.jpeg" alt="User" />
    <input type="text" bind:value={userFeed} {placeholder} />
  </div>
  <button on:click={() => {}}>Tweet</button>
</div>
<hr />
