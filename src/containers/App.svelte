<script>
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  import Sidebar from "../components/Sidebar.svelte";
  import Footer from "../components/Footer.svelte";
  import { isDarkModeActive } from "../store/store.js";

  isDarkModeActive.subscribe(value => {
    value
      ? document.body.classList.add("dark")
      : document.body.classList.remove("dark");
  });
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&display=swap");
  @import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");

  :global(:root) {
    --light-theme-body-background: #ebedf0;
    --dark-theme-body-background: #1c1e21;
    --white-color: #fff;
    --black-color: #000;
    --dark-parts-color: #242526;
    --gray-color: rgb(38, 38, 38);
    --gray-alpha-20: rgba(38, 38, 38, 0.2);
    --gray-alpha-40: rgba(38, 38, 38, 0.4);
    --gray-alpha-60: rgba(38, 38, 38, 0.6);
    --gray-alpha-80: rgba(38, 38, 38, 0.8);
    --blue-color: rgb(60, 110, 181);
    --blue-alpha-20: rgba(60, 110, 181, 0.2);
    --blue-alpha-40: rgba(60, 110, 181, 0.4);
    --blue-alpha-60: rgba(60, 110, 181, 0.6);
    --blue-alpha-80: rgba(60, 110, 181, 0.8);
  }

  :global(body) {
    background-color: var(--light-theme-body-background);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    transition: .3s ease;
  }

  :global(body.dark) {
    background-color: var(--dark-theme-body-background);
    color: var(--white-color);
  }

  :global(textarea, input) {
    font-family: "Lato", sans-serif;
  }

  :global(ul) {
    list-style: none;
  }

  :global(a) {
    text-decoration: none;
    color: var(--light-texts-color);
  }

  :global(a):active {
    color: var(--gray-alpha-80);
  }

  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }

  :global(small) {
    font-size: 11px;
  }
</style>

<Header />
<Main>
  <TimeLine />
  <Sidebar />
</Main>
