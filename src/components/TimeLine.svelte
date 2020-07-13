<script>
  import Card from "./Card.svelte";
  import { isDarkMode } from "../store/store.js";

  export let posts = [];
  export let locations = [];
  export let descriptions = [];
  export let comments = [];
</script>

<style>
  .time-line {
    max-width: 642px;
    width: 100%;
  }

  .loader {
    width: 40px;
    height: 40px;
    margin: 100px auto;
    background-color: rgba(51, 51, 51, 0.6);
    border-radius: 100%;
    animation: scale-out 1s ease-in-out infinite alternate;
  }

  @keyframes scale-out {
    0% {
      transform: scale(0);
    }
    100% {
      transform: scale(1);
    }
  }

  .loader-dark {
    background-color: rgba(204, 204, 204, 0.6);
  }
</style>

<div class="time-line">
  {#each posts as post}
    <Card
      username={post.user}
      usernameFooter={post.user}
      userImg={post.userImageURL}
      photo={post.webformatURL}
      {locations}
      {descriptions}
      {comments} />
  {:else}
    <div class="loader" class:loader-dark={$isDarkMode} />
  {/each}
</div>
