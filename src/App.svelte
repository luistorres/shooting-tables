<script>
  import Table from "./Table.svelte";
  import { onDestroy } from "svelte";

  let counter = 0;
  const interval = setInterval(() => {
    counter += 1;
  }, 30);

  onDestroy(() => clearInterval(interval));
</script>

<style>
  .main {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .video {
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .tableWrapper {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
  }

  .table {
    top: 0;
  }
  svg {
    width: 100%;
    height: 100%;
    margin: -8px;
  }
  circle {
    fill: #ff3e00;
    z-index: 10;
  }
</style>

<div class="main">
  <div class="video">
    <iframe
      width="100%"
      height="100%"
      src="https://www.youtube.com/embed/usf3mcXE7Ro?autoplay=1"
      frameborder="0"
      allow="accelerometer; autoplay; encrypted-media; gyroscope;
      picture-in-picture"
      allowfullscreen />
  </div>
  <div
    class="tableWrapper"
    style="transform: translate({counter}px, {counter / 2}px)">
    <div class="table" style="transform: rotate({counter * 5}deg)">
      <Table angle={counter} />
    </div>
  </div>
</div>
