<script context="module">
  export async function preload({ params, query }) {
    const res = await this.fetch(`http://localhost:3000/tweets/${params.slug}`);
    const userInfo = await res.json();
    return { userInfo };
  }
</script>

<script>
  import Image from "../../components/Image.svelte";
  import FaMapMarkerAlt from "svelte-icons/fa/FaMapMarkerAlt.svelte";
  import MdMap from "svelte-icons/md/MdMap.svelte";

  export let userInfo;
</script>

<style>
  main {
    border: 1px solid #e6ecf0;
    text-align: center;
    padding-bottom: 1.5em;
    max-width: 240px;
    align-self: center;
    width: 600px;
    margin: 0 auto;
  }
  .container {
    flex-direction: column;
    display: flex;
  }
  .content {
    text-align: left;
    margin-left: 1em;
  }
  .img-container {
    flex-direction: row;
    display: flex;
    justify-content: space-between;
  }
  .username {
    color: rgb(109, 108, 108);
  }
  button {
    border-radius: 25px;
    background-color: rgb(23, 191, 99);
    padding: 10px;
    color: white;
    font-size: 15px;
    width: 20%;
    height: 5%;
    margin: 0.25em;
    margin-right: 1em;
    align-self: center;
  }
  button:hover {
    background-color: rgb(24, 207, 107);
  }
  .icon {
    width: 20px;
    height: 20px;
    color: rgb(196, 191, 191);
  }
  .details {
    flex-direction: row;
    display: flex;
  }
  span {
    margin-right: 2em;
  }
  #location {
    flex-direction: row;
    display: flex;
  }
  h2 {
    margin-bottom: 0;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<svelte:head>
  <title>User Profile</title>
</svelte:head>

<main>
  <div class="container">
    <Image
      src={userInfo.user.cover}
      alt="user-cover"
      type="cover"
      height="275px"
      width="100%" />

    <div class="img-container">
      <Image
        className={'border-radius:50px'}
        src={userInfo.user.avatar}
        alt="user-avatar"
        type="avatar"
        height="100px"
        width="100px" />
      <button on:click={() => {}}>Follow</button>

    </div>
    <div class="content">
      <h2>{userInfo.user.name}</h2>
      <span class="username">@{userInfo.user.username}</span>
      <p>{userInfo.user.bio}</p>
      <div class="details">
        <span id="location">
          <div class="icon">
            <FaMapMarkerAlt />
          </div>
          {userInfo.user.location}
        </span>
        <span>{userInfo.user.followers} Followers</span>
        <span>{userInfo.user.following} Following</span>
      </div>
    </div>
  </div>
</main>
