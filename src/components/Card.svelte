<script>
  import Comments from "./Comments.svelte";
  import { isDarkModeActive } from "../store/store.js";
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

  /* Estilo común */
  .card__username {
    font-size: 14px;
    font-weight: bold;
  }
</style>

<article class="card" class:card-dark={$isDarkModeActive}>
  <!-- Header -->
  <header class="card__header">
    <div class="card__user">
      <div class="card__profile">
        <a href="/#" class="card__link">
          <img
            src="./src/images/profile-mariop.jpeg"
            alt="perfil"
            class="card__perfil" />
        </a>
      </div>
      <h2 class="card__username-header card__username">
        <a href="/#" class="card__link">mappedev</a>
        <span class="card__ubication" class:card-ubication-dark={$isDarkModeActive}>Caracas, Venezuela</span>
      </h2>
    </div>
    <div class="card__settings">
      <i class="fas fa-ellipsis-h card__icon card__icon-settings" />
    </div>
  </header>

  <!-- Photo -->
  <figure class="card__photo">
    <img
      src="./src/images/platzi-course-svelte-with-oscar.jpg"
      alt="svelte course with oscar"
      class="card__img" />
  </figure>

  <!-- Icons -->
  <div class="card__icons">
    <div class="card__icons-left">
      <i class="fas fa-heart card__icon card__icon-heart" />
      <i class="fas fa-paper-plane card__icon card__icon-plane" />
    </div>
    <div class="card__icons-right">
      <i class="fas fa-bookmark card__icon card__icon-bookmark" />
    </div>
  </div>

  <!-- Description -->
  <div class="card__description">
    <a href="/#" class="card__link">
      <h2 class="card__username-description card__username">mappedev</h2>
    </a>
    <span class="card__description-text" class:card-description-text-dark={$isDarkModeActive}>Excelente curso, ¡Lo recomiendo!</span>
  </div>

  <!-- Comments -->
  <!-- Lo separamos porque tiene algo de lógica... -->
  <Comments />
</article>
