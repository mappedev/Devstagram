<script>
  import Modal from "./Modal.svelte";
  import Share from "./Share.svelte";
  import Comments from "./Comments.svelte";
  import { isDarkMode } from "../store/store.js";
  import { likeCount } from "../store/store.js";
  import { blur } from "svelte/transition";

  export let username;
  export let usernameFooter;
  export let userImg;
  export let photo;
  export let locations;
  export let descriptions;
  export let comments;

  const handleLike = () => {
    isLike = !isLike;

    if (isLike) {
      $likeCount++;
    } else {
      $likeCount--;
    }
  }

  const handleDoubleLike = () => {
    if (!isLike) {
      isLike = true;
      $likeCount++;
    }
  }

  let isModal = false;
  let isLike = false;
  let isBookmark = false;

  let description =
    descriptions[Math.floor(Math.random() * descriptions.length)];
</script>

<style>
  .card {
    border: 1px solid var(--gray-alpha-20);
    border-radius: 4px;
    background-color: var(--white-color);
    margin-bottom: 60px;
  }

  .card-dark {
    background-color: var(--dark-parts-color);
    color: var(--white-color);
  }

  .card__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px;
  }

  .card__user {
    display: flex;
  }

  .card__perfil {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }

  .card__username-header {
    margin-left: 14px;
  }

  .card__ubication {
    font-size: 12px;
    color: var(--gray-alpha-60);
    display: block;
  }

  .card-ubication-dark {
    color: var(--white-color);
  }

  .card__photo {
    margin: 0;
    cursor: pointer;
  }

  .card__img {
    width: 100%;
    height: auto;
  }

  .card__icons {
    padding: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .card__icon {
    cursor: pointer;
  }

  .card__icon-plane {
    margin-left: 10px;
  }

  .bookmark-active {
    color: orange;
  }

  .heart-active {
    color: #bc1888;
    animation: bounce linear 0.8s 1;
    transform-origin: 20% 20%;
  }

  @keyframes bounce {
    0% {
      transform: translateY(0);
    }

    15% {
      transform: translateY(-25px);
    }

    30% {
      transform: translateY(0);
    }

    45% {
      transform: translateY(-15px);
    }

    60% {
      transform: translateY(0);
    }

    75% {
      transform: translateY(-5px);
    }

    100% {
      transform: translateY(0);
    }
  }

  .card__description {
    display: flex;
    align-items: center;
    padding: 0 16px;
  }

  .card__description-text {
    font-size: 14px;
    color: var(--gray-color);
    margin-left: 5px;
  }

  .card-description-text-dark {
    color: var(--white-color);
  }

  .card__username {
    font-size: 14px;
    font-weight: bold;
  }
</style>

<article class="card" class:card-dark={$isDarkMode}>
  <!-- Modal -->
  {#if isModal}
    <div transition:blur>
      <Modal on:click={() => (isModal = !isModal)}>
        <Share on:click={() => (isModal = !isModal)} />
      </Modal>
    </div>
  {/if}
  <!-- Header -->
  <header class="card__header">
    <div class="card__user">
      <div class="card__profile">
        <a href="/#" class="card__link">
          <img src={userImg} alt={username} class="card__perfil" />
        </a>
      </div>
      <h2 class="card__username-header card__username">
        <a href="/#" class="card__link">{username}</a>
        <span
          class="card__ubication"
          class:card-ubication-dark={$isDarkMode}>
          {locations[Math.floor(Math.random() * locations.length)]}
        </span>
      </h2>
    </div>
    <div class="card__settings">
      <i class="fas fa-ellipsis-h card__icon card__icon-settings" />
    </div>
  </header>

  <!-- Photo -->
  <figure class="card__photo" on:dblclick={handleDoubleLike}>
    <img src={photo} alt="post-img" class="card__img" />
  </figure>

  <!-- Icons -->
  <div class="card__icons">
    <div class="card__icons-left">
      <i
        class="fas fa-heart card__icon card__icon-heart"
        class:heart-active={isLike}
        on:click={handleLike} />
      <i
        class="fas fa-paper-plane card__icon card__icon-plane"
        on:click={() => (isModal = !isModal)} />
    </div>
    <div class="card__icons-right">
      <i
        class="fas fa-bookmark card__icon card__icon-bookmark"
        class:bookmark-active={isBookmark}
        on:click={() => (isBookmark = !isBookmark)} />
    </div>
  </div>

  <!-- Description -->
  <div class="card__description">
    <a href="/#" class="card__link">
      <h2 class="card__username-description card__username">{username}:</h2>
    </a>
    <span
      class="card__description-text"
      class:card-description-text-dark={$isDarkMode}>
      {description}
    </span>
  </div>

  <!-- Comments -->
  <Comments {comments} user={usernameFooter} />
</article>
