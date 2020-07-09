<script>
  import { isDarkModeActive } from "../store/store.js";
</script>

<style>
  .header {
    background-color: var(--white-color);
    position: fixed;
    width: 100%;
    height: 53px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: 1px solid var(--gray-alpha-20);
    outline: none;
    z-index: 1;
  }

  .header-dark {
    background-color: var(--dark-parts-color);
    border-bottom: 1px solid #404040;
  }

  .header__container {
    display: grid;
    align-items: center;
    grid-template-columns: minmax(auto, 935px);
    justify-content: space-evenly;
    padding: 0 20px;
  }

  .header__content {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .logo__text {
    font-family: "Pacifico", cursive;
    font-size: 28px;
    position: relative;
    background: linear-gradient(to right, #12cad6, #5c2a9d);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    color: #3c6eb5;
  }

  .menu__list {
    display: flex;
    align-items: center;
    font-size: var(--header-icons-size-px);
  }

  .menu__item {
    margin: 0 10px;
  }

  .menu__item:last-child {
    margin: 0 0 0 10px;
  }

  .menu__perfil {
    width: 27px;
    height: 27px;
    border-radius: 50%;
  }
</style>

<header class="header" class:header-dark={$isDarkModeActive}>
  <div class="header__container">
    <div class="header__content">
      <div class="logo">
        <a href="/" class="logo__link">
          <h1 class="logo__text">Devstagram</h1>
        </a>
      </div>

      <nav class="menu">
        <ul class="menu__list">
          <li class="menu__item">
            <a href="/#" class="menu__link">
              <i class="fas fa-heart menu__icon" />
            </a>
          </li>
          <li class="menu__item">
            <a href="/#" class="menu__link">
              <i class="fas fa-user-alt menu__icon" />
            </a>
          </li>
          <li class="menu__item">
            <a href="/#" class="memu_link">
              <img
                src="./src/images/profile-mariop.jpeg"
                alt="perfil"
                class="menu__perfil" />
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</header>
