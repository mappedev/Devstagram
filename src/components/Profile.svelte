<script>
  import { isDarkModeActive } from "../store/store.js";

  const changeMode = () => ($isDarkModeActive = !$isDarkModeActive);
</script>

<style>
  .profile {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0 16px;
    box-sizing: border-box;
  }

  .profile__data {
    display: flex;
    align-items: center;
  }

  .profile__img {
    width: 56px;
    height: 56px;
    border-radius: 50%;
  }

  .profile__info {
    padding-left: 15px;
  }

  .profile__username {
    font-size: 14px;
    font-weight: bold;
  }

  .profile__name {
    font-size: 12px;
    font-weight: 400;
  }

  .profile__switch {
    background: linear-gradient(to right, #12cad6, #5c2a9d);
    border-radius: 100px;
    border: none;
    position: relative;
    cursor: pointer;
    outline: none;
    padding: 0;
    display: flex;
  }

  .profile__switch:after {
    content: "";
    width: 30px;
    height: 30px;
    border-radius: 100px;
    background-color: #f1f1f1;
    position: absolute;
    left: 0;
    box-shadow: 0px 0px 2px 2px rgba(0, 0, 0, 0.2);
    transition: transform linear .3s;
  }

  .profile__switch.active:after {
    transform: translateX(30px);
  }

  .profile__icon {
    width: 30px;
    height: 30px;
    line-height: 30px;
    color: var(--white-color);
  }
</style>

<div class="profile">
  <div class="profile__data">
    <div class="profile__avatar">
      <a href="/#" class="profile__link-avatar">
        <img
          src="./src/images/profile-mariop.jpeg"
          alt="perfil"
          class="profile__img" />
      </a>
    </div>
    <div class="profile__info">
      <a href="/#" class="profile__link-username">
        <h2 class="profile__username">mappedev</h2>
      </a>
      <span class="profile__name">Mario Peña</span>
    </div>
  </div>
  <button
    class="profile__switch"
    class:active={$isDarkModeActive}
    on:click={changeMode}>
    <i class="fas fa-sun profile__icon" />
    <i class="fas fa-moon profile__icon" />
  </button>
</div>
