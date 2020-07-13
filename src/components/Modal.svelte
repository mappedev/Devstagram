<style>
  .modal {
    position: relative;
  }
  .modal__overlay {
    background-color: rgba(0, 0, 0, 0.6);
    position: fixed;
    /* width: 100%;
    height: 100%; */
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 2;
    cursor: pointer;
  }
</style>

<div class="modal">
  <div class="modal__overlay" on:click />
  <slot />
</div>