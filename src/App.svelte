<script>
  import Header from "./components/Header.svelte";
  import UserHeader from "./components/UserHeader.svelte";
  import Post from "./components/Post.svelte";

  import { tweets } from "./store.js";

  let myTweets = getTweets();

  async function getTweets() {
    const response = await fetch("http://localhost:3000/tweets");
    const tweet = await response.json();
    tweets.set(tweet);
    if (response.ok) {
      return tweet;
    } else {
      throw new Error(tweet);
    }
  }
</script>

<style>
  main {
    border-left: 1px solid #e6ecf0;
    border-right: 1px solid #e6ecf0;
    text-align: center;
    padding: 0;
    padding-bottom: 0.75em;
    max-width: 240px;
    align-self: center;
    width: 600px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <Header />
  <UserHeader />
  {#await myTweets}
    <p>Loading...</p>
  {:then mytweets}
    {#if mytweets !== undefined}
      <Post tweet={mytweets} />
    {/if}
  {:catch error}
    {error.message}
  {/await}
</main>
