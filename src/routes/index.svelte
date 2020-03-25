<script context="module">
  export function preload({ page, session }) {
    return this.fetch("http://localhost:3000/tweets")
      .then(r => r.json())
      .then(mytweets => {
        let tweetList = mytweets.reverse();
        return { tweetList };
      });
  }
</script>

<script>
  import Header from "../components/Header.svelte";
  import UserHeader from "../components/UserHeader.svelte";
  import Post from "../components/Post.svelte";
  import { onMount } from "svelte";

  import { tweets } from "../store.js";
  export let tweetList;
  tweets.set(tweetList);
</script>

<style>
  main {
    border-left: 1px solid #e6ecf0;
    border-right: 1px solid #e6ecf0;
    border-top: 1px solid #e6ecf0;
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

<svelte:head>
  <title>Twitter Sample</title>
</svelte:head>

<main>
  <Header />
  <UserHeader />
  {#await tweetList}
    <p>Loading...</p>
  {:then tweetList}
    {#if tweetList !== undefined}
      <Post />
    {/if}
  {:catch error}
    {error.message}
  {/await}
</main>
