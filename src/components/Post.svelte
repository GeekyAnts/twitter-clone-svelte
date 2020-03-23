<script>
  import Image from "./Image.svelte";

  import MdRepeat from "svelte-icons/md/MdRepeat.svelte";
  import MdArrowUpward from "svelte-icons/md/MdArrowUpward.svelte";
  import GoComment from "svelte-icons/go/GoComment.svelte";
  import IoIosHeartEmpty from "svelte-icons/io/IoIosHeartEmpty.svelte";

  import { tweets } from "../store.js";
</script>

<style>
  .card-container {
    flex-direction: row;
    display: flex;
    justify-content: space-around;
    border-bottom: 1px solid #e6ecf0;
  }
  .content {
    margin: 0.5em;
    flex-direction: column;
    flex: 1;
    text-align: left;
  }
  .body {
    flex-direction: column;
    margin-bottom: 2em;
  }
  .header {
    margin-top: 0.5em;
    margin-bottom: 0.5em;
  }
  .footer {
    margin-bottom: 1em;
    flex-direction: row;
    display: flex;
    justify-content: space-around;
  }
  #name {
    font-weight: bold;
  }
  .main-context {
    margin-bottom: 1em;
  }
  .icon {
    width: 25px;
    height: 25px;
  }
  .repeat {
    transform: rotate(90deg);
  }
  button {
    padding: 0;
    border: none;
    background: none;
  }
</style>

{#each $tweets as tweet}
  <div class="card-container">
    <Image src={tweet.user.avatar} type="profile" alt="profile" />
    <div class="content">
      <div class="header">
        <span id="name">{tweet.user.name}</span>
        @{tweet.user.username}
      </div>
      <div class="body">
        <div class="main-context">{tweet.tweetContent}</div>
        {#if tweet.user.cover}
          <Image
            src={tweet.user.cover}
            type="content"
            alt="content"
            height="275px"
            width="100%" />
        {/if}
      </div>
      <div class="footer">
        <button on:click={() => {}} class="icon">
          <GoComment />
        </button>
        <button on:click={() => {}} class="icon">
          <IoIosHeartEmpty />
        </button>
        <button on:click={() => {}} class="icon repeat">
          <MdRepeat />
        </button>
        <button on:click={() => {}} class="icon">
          <MdArrowUpward />
        </button>
      </div>
    </div>
  </div>
{/each}
