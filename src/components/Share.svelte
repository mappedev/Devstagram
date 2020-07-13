<script>
  import { isDarkMode } from "../store/store.js";
</script>

<style>
  .share {
    border-radius: 4px;
    background-color: var(--white-color);
    color: var(--black-color);
    margin: 0 0 2em 0;
    width: 300px;
    position: absolute;
    top: 300px;
    left: 25%;
    z-index: 3;
    padding: 1em;
  }

  .share-dark {
    background-color: var(--dark-parts-color); 
    color: var(--white-color);
  }

  .share__head {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .share__title {
    font-size: 16px;
  }

  .share__exit {
    cursor: pointer;
  }

  .share__link {
    display: flex;
    align-items: center;
    text-decoration: none;
    font-size: 14px;
    margin: 2em 0 0 0;
  }

  .share__icon-social {
    color: #3b5998;
    margin: 0 0.5em 0 0;
    font-size: 20px;
  }
</style>

<div class="share" class:share-dark={$isDarkMode}>
  <div class="share__head">
    <h2 class="share__title">Compartir</h2>
    <i class="fas fa-times-circle share__exit" on:click />
  </div>
  <div class="share__content">
    <a
      href="https://www.facebook.com/sharer.php?&t=Aprendiendo%20a%20crear%20un%20enlace%20para%20compartir%20en%20Facebook%20https://devstagram.com/&u=https://devstagtam.com"
      target="_blank"
      class="share__link">
      <i class="fab fa-facebook-square share__icon-social" />
      Compartir en Facebook
    </a>
    <a
      href="https://twitter.com/intent/tweet?text=Aprendiendo%20a%20crear%20un%20enlace%20para%20compartir%20en%20Twitter&url=devstagram.com"
      target="_blank"
      class="share__link">
      <i class="fab fa-twitter-square share__icon-social" />
      Compartir en Twitter
    </a>
    <a
      href="https://api.whatsapp.com/send?&text=Aprendiendo%20a%20crear%20un%20enlace%20para%20compartir%20en%20Whatsapp%20https://devstagram.com/"
      target="_blank"
      class="share__link">
      <i class="fab fa-whatsapp-square share__icon-social" />
      Compartir en Whatsapp
    </a>
  </div>
</div>
