<script lang="ts">
  import { onMount } from "svelte";
  import * as THREE from "three";
  import { WebGLUtils } from "three";
  const webglUtils = new WebGLUtils();
  webglUtils.convert();

  onMount(() => {});
</script>

<div>
  <div>Volume Rendering</div>
  <div id="canvas-container" />
</div>
