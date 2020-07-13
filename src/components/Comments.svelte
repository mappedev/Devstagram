<script>
  import { isDarkMode } from "../store/store.js";

  export let user;
  export let comments;

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

  const addComment = event => {
    const msg = event.target.text.value;

    newComments = [...newComments, msg];

    // Reset:
    event.target.text.value = "";   
    inputIsValid = false;
    resize(textarea);
  };

  let inputIsValid = null;
  let userInverted = "";
  let x = user.length;
  let textarea;
  let comment = [comments[Math.floor(Math.random() * comments.length)]];
  let newComments = [];

  while (x >= 0) {
    userInverted += user.charAt(x);
    x--;
  }
</script>

<style>
  .comments__container {
    /* display: flex;
    align-items: center; */
    padding: 16px 16px 8px;
    border-bottom: 1px solid #dddddd;
  }

  .comments-container-dark {
    border-bottom: 1px solid #404040;
  }

  .comment__content {
    display: flex;
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
    cursor: pointer;
  }

  .input-invalid {
    color: var(--blue-alpha-40);
  }
</style>

<div class="comments">
  <div
    class="comments__container"
    class:comments-container-dark={$isDarkMode}>
    <div class="comment__content">
      <a href="/#" class="card__link">
        <h2 class="comments__username">{userInverted}:</h2>
      </a>
      <span
        class="comments__comment"
        class:comments-comment-dark={$isDarkMode}>
        {comment}
      </span>
    </div>
    {#each newComments as comment}
      <div class="comment__content">
        <a href="/#" class="card__link">
          <h2 class="comments__username">mappedev:</h2>
        </a>
        <span
          class="comments__comment"
          class:comments-comment-dark={$isDarkMode}>
          {comment}
        </span>
      </div>
    {/each}
  </div>

  <form class="comments__add" on:submit|preventDefault={addComment}>
    <textarea
      type="text"
      placeholder="Agrega un comentario..."
      class="comments__input"
      id="text"
      on:input|preventDefault={inputFunctions}
      bind:this={textarea}
      class:comments-input-dark={$isDarkMode} />
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
