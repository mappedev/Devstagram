<script>
  import TimeLine from "./TimeLine.svelte";
  import Sidebar from "./Sidebar.svelte";
  import { onMount } from "svelte";

  export let data;
  export let locations;
  export let descriptions;
  export let comments;
  export let nickname;
  export let name;

  let refTimeline;
  let refStories;

  onMount(() => {
    if (window.matchMedia("(max-width:999px)").matches) {
      console.log("Hora de cambiar de posición");
      refTimeline = "timeline";
      refStories = "stories";
    }
  });
</script>

<style>
  .main {
    display: grid;
    justify-content: center;
    grid-template-columns: minmax(auto, 935px);
    padding: 0 20px;
  }

  :global(.main__container) {
    display: grid;
    grid-template-columns: minmax(auto, 642px) minmax(auto, 293px);
    gap: 28px;
    padding-top: 83px;
    grid-template-areas: "timeline stories";
  }

  @media (max-width: 999px) {
    .main__container {
      grid-template: auto 1fr / 1fr;
      grid-template-areas:
        "stories"
        "timeline";
    }
  }
</style>

<div class="main">
  <div class="main__container">
    <TimeLine posts={data.hits} {locations} {descriptions} {comments} />
    <Sidebar {nickname} {name} />
  </div>
</div>
