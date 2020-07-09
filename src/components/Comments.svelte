<script>
  import { isDarkModeActive } from "../store/store.js";

  const validateCamp = target => {
    if (target.value.length === 0 || /^\s+$/.test(target.value)) {
      return (inputIsValid = false);
    } else {
      return (inputIsValid = true);
    }
  };

  const resize = target => {
    target.style.height = "0px";
    target.style.height = `${target.scrollHeight}px`;
  };

  const inputFunctions = ({ target }) => {
    validateCamp(target);
    resize(target);
  };

  const validateInput = el => {
    el.addEventListener("input", inputFunctions);
  };

  let inputIsValid = null;
</script>

<style>
  .comments__friends {
    display: flex;
    align-items: center;
    padding: 16px 16px 8px;
    border-bottom: 1px solid #dddddd;
  }

  .comments-friends-dark {
    border-bottom: 1px solid #404040;
  }

  .comments__username {
    font-size: 14px;
    font-weight: bold;
  }

  .comments__comment {
    font-size: 14px;
    color: var(--gray-color);
    margin-left: 5px;
  }

  .comments-comment-dark {
    color: var(--white-color);
  }

  .comments__add {
    padding: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .comments__input {
    border: none;
    background-color: var(--white-color);
    font-size: 14px;
    width: 100%;
    margin-right: 10px;
    max-height: 80px;
    resize: none;
    border: none;
    outline: none;
  }

  .comments-input-dark {
    background-color: transparent;
    color: white;
  }

  .comments__submit {
    padding: 10px;
    font-size: 14px;
    font-weight: bold;
    border: none;
    outline: none;
    background: none;
  }

  .comments__submit:active {
    color: var(--blue-alpha-80);
  }
  
  .input-valid {
    color: var(--blue-color);
  }

  .input-invalid {
    color: var(--blue-alpha-40);
  }
</style>

<div class="comments">
  <div class="comments__friends" class:comments-friends-dark={$isDarkModeActive}>
    <a href="/#" class="card__link">
      <h2 class="comments__username">rosa_cod3</h2>
    </a>
    <span class="comments__comment" class:comments-comment-dark={$isDarkModeActive}>Tremendo framework.</span>
  </div>

  <form class="comments__add">
    <!-- Usaremos "use:validateInput" para hacer resize del campo y activar el botón cuando haya algún dato. -->
    <!-- En caso de hacer una sola acción en el campo, pudimos haber usado on:input={function} y directamente la acción a tomar. -->
    <textarea
      type="text"
      placeholder="Agrega un comentario..."
      class="comments__input"
      id="text"
      use:validateInput 
      class:comments-input-dark={$isDarkModeActive} />
    <button
      type="submit"
      class="comments__submit"
      disabled={!inputIsValid}
      class:input-valid={inputIsValid}
      class:input-invalid={!inputIsValid}>
      Publicar
    </button>
  </form>
</div>
