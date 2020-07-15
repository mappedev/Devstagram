<script>
  import { isDarkMode } from "../store/store.js";

  let isFavorite = false;
</script>

<style>
  .stories {
    background-color: var(--white-color);
    border-radius: 15px;
  }

  .stories-dark {
    background-color: var(--dark-parts-color);
    color: var(--white-color);
  }

  .stories__header {
    padding: 12px 16px 6px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .stories__title {
    font-size: 14px;
    font-weight: bold;
    color: var(--gray-alpha-60);
  }

  .stories-title-dark {
    color: var(--white-color);
  }

  .stories__more {
    font-size: 12px;
    font-weight: bold;
  }

  .stories__items {
    padding: 6px 16px 12px;
  }

  .stories__item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 5px;
  }

  .stories__data-user {
    display: flex;
  }

  .stories__avatar {
    border-radius: 50%;
    border: 2px solid rgb(20, 161, 255);
    background-color: var(--white-color);
  }

  .stories__img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    border: 1px solid var(--white-color);
    outline: none;
  }

  .stories__user-info {
    padding-left: 10px;
  }

  .stories__username {
    font-size: 14px;
    font-weight: 600;
  }

  .stories__time {
    font-size: 12px;
    font-weight: 400;
    color: var(--gray-alpha-60);
  }

  .stories-time-dark {
    color: var(--white-color);
  }

  .stories__icon-favorites {
    cursor: pointer;
  }

  .stories__icon-favorites.active {
    color: orange;
  }
</style>

<div class="stories" class:stories-dark={$isDarkMode}>
  <div class="stories__header">
    <h2 class="stories__title" class:stories-title-dark={$isDarkMode}>
      Historias recientes
    </h2>
    <a href="/#" class="stories__link-more">
      <span class="stories__more">Ver todas</span>
    </a>
  </div>

  <div class="stories__items">
    <div class="stories__item">
      <div class="stories__data-user">
        <div class="stories__avatar">
          <a href="/#" class="stories__link-user">
            <img
              src="https://img.icons8.com/dusk/452/user-female-skin-type-1-2.png"
              alt="perfil"
              class="stories__img" />
          </a>
        </div>
        <div class="stories__user-info">
          <a href="/#" class="stories__link-username">
            <h2 class="stories__username">susana7dev7</h2>
          </a>
          <span class="stories__time" class:stories-time-dark={$isDarkMode}>
            hace 24 minutos
          </span>
        </div>
      </div>
      <div class="stories__favorite">
        <i
          class="fas fa-star stories__icon-favorites"
          class:active={isFavorite}
          on:click={() => (isFavorite = !isFavorite)} />
      </div>
    </div>
  </div>
</div>
