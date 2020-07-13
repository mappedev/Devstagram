<style>
  .main {
    display: grid;
    justify-content: center;
    grid-template-columns: minmax(auto, 935px);
    padding: 0 20px;
  }

  .main__container {
    display: grid;
    grid-template-columns: minmax(auto, 642px) minmax(auto, 293px);
    gap: 28px;
    padding-top: 83px;
  }
</style>

<div class="main">
  <div class="main__container">
    <slot />
  </div>
</div>
