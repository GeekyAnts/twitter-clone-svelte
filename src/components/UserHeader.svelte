<script>
  import Image from "./Image.svelte";
  import { tweets } from "../store.js";
  import faker from "faker";

  let userFeed = "";
  let user = {
    name: "Geekyants",
    username: "geekyants",
    avatar: "user.jpeg",
    cover: "great-success.png",
    bio: "Svelte Developer",
    location: "Delhi",
    following: 3,
    followers: 10
  };
  let placeholder = "What's happening?";
  let payload;
  async function tweetPost() {
    payload = {
      id: faker.random.number(100000),
      user: user,
      time: new Date().toISOString(),
      tweetContent: userFeed,
      likes: 0,
      retweets: 0,
      replies: 0
    };
    userFeed = "";
    const response = await fetch("http://localhost:3000/tweets", {
      method: "post",
      headers: {
        Accept: "application/json, text/plain, */*",
        "Content-Type": "application/json"
      },
      body: JSON.stringify(payload)
    })
      .then(res => res.json())
      .then(res => {
        tweets.update(tweet => {
          const mytweet = [payload, ...tweet];
          return mytweet;
        });
      });
  }
</script>

<style>
  .header {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin-top: 2em;
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
  input {
    font-size: 20px;
  }
  input::placeholder {
    font-size: 20px;
    color: #9197a3;
    font-family: Arial, Helvetica, sans-serif;
  }
  button {
    outline: none;
    border: none;
    border-radius: 25px;
    background-color: rgb(23, 191, 99);
    padding: 10px;
    color: white;
    width: 20%;
    margin: 0.25em;
    align-self: flex-end;
    font-size: 15px;
  }
  button:hover {
    background-color: rgb(24, 207, 107);
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
  <button on:click={tweetPost}>Tweet</button>
</div>
<hr />
