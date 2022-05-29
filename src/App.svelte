<script lang="ts">
  import router from "page";
  import Home from "./pages/Home.svelte";
  import About from "./pages/About.svelte";
  import FirstThreeJs from "./pages/FirstThreeJs.svelte";
  import MeshRendering from "./pages/MeshRendering.svelte";
  import BasicWebGlTriangle from "./pages/BasicWebGlTriangle.svelte";
  import BasicWebGlRectangle from "./pages/BasicWebGlRectangle.svelte";
  import BasicWebGlManyRectangles from "./pages/BasicWebGlManyRectangles.svelte";

  // page router settings
  let page;
  router("/", () => (page = Home));
  router("/about", () => (page = About));
  router("/first-threejs", () => (page = FirstThreeJs));
  router("/mesh-rendering", () => (page = MeshRendering));
  router("/basic-webgl-triangle", () => (page = BasicWebGlTriangle));
  router("/basic-webgl-rectangle", () => (page = BasicWebGlRectangle));
  router(
    "/basic-webgl-many-rectangles",
    () => (page = BasicWebGlManyRectangles)
  );
  router.start();

  export let name: string;
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
  <svelte:component this={page} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
