<script lang="ts">
  import router from "page";
  import Home from "./components/Home.svelte";
  import About from "./components/About.svelte";
  import Prototype from "./components/Prototype.svelte";

  let page;
  router("/", () => (page = Home));
  router("/about", () => (page = About));
  router("/prototype", () => (page = Prototype));

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
