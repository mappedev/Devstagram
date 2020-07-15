<script>
  import Profile from "./Profile.svelte";
  import Stories from "./Stories.svelte";
  import Footer from "./Footer.svelte";

  export let nickname;
  export let name;
</script>

<style>
  .sidebar {
    position: relative;
    grid-area: stories;
  }

  .sidebar__container {
    display: grid;
    grid-template-rows: auto 1fr auto;
    gap: 20px;
    position: fixed;
    max-width: 293px;
    width: 100%;
  }

  @media (max-width: 999px) {
    .sidebar__container {
      position: static;
      margin: 0 auto;
    }
  }
</style>

<aside class="sidebar">
  <div class="sidebar__container">
    <Profile {nickname} {name} />
    <Stories />
    <Footer />
  </div>
</aside>
