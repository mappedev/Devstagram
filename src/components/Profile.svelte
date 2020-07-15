<script>
  import { isDarkMode } from "../store/store.js";

  export let nickname;
  export let name;

  const changeMode = () => ($isDarkMode = !$isDarkMode);
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
    background: linear-gradient(to right, #4ee8f3, #270e47);
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
    background-color: var(--white-color);
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
          src="https://pbs.twimg.com/profile_images/1259184766932398080/tNoYzDpS_400x400.jpg"
          alt="perfil"
          class="profile__img" />
      </a>
    </div>
    <div class="profile__info">
      <a href="/#" class="profile__link-username">
        <h2 class="profile__username">{nickname}</h2>
      </a>
      <span class="profile__name">{name}</span>
    </div>
  </div>
  <button
    class="profile__switch"
    class:active={$isDarkMode}
    on:click={changeMode}>
    <i class="fas fa-sun profile__icon" />
    <i class="fas fa-moon profile__icon" />
  </button>
</div>
