<script lang="ts">
  import { onMount } from "svelte";
  import * as THREE from "three";
  import { OrbitControls } from "three/examples/jsm/controls/OrbitControls.js";

  onMount(() => {
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document
      .getElementById("canvas-container")
      .appendChild(renderer.domElement);

    const geometry = new THREE.BufferGeometry();
    // create a simple square shape. We duplicate the top left and bottom right
    // vertices because each vertex needs to appear once per triangle.
    const vertices = new Float32Array([
      -1.0, -1.0, 1.0, 1.0, -1.0, 1.0, 1.0, 1.0, 1.0,

      1.0, 1.0, 1.0, -1.0, 1.0, 1.0, -1.0, -1.0, 1.0,

      1.0, 1.0, -1.0, 1.0, -1.0, -1.0, -1.0, -1.0, -1.0,

      -1.0, -1.0, -1.0, -1.0, 1.0, -1.0, 1.0, 1.0, -1.0,

      1.0, 1.0, -1.0, -1.0, 1.0, 1.0, 1.0, 1.0, 1.0,

      1.0, 1.0, -1.0, -1.0, 1.0, -1.0, -1.0, 1.0, 1.0,

      1.0, -1.0, 1.0, -1.0, -1.0, 1.0, 1.0, -1.0, -1.0,

      -1.0, -1.0, 1.0, -1.0, -1.0, -1.0, 1.0, -1.0, -1.0,

      1.0, 1.0, 1.0, 1.0, -1.0, 1.0, 1.0, 1.0, -1.0,

      1.0, -1.0, -1.0, 1.0, 1.0, -1.0, 1.0, -1.0, 1.0,

      -1.0, 1.0, -1.0, -1.0, -1.0, 1.0, -1.0, 1.0, 1.0,

      -1.0, -1.0, 1.0, -1.0, 1.0, -1.0, -1.0, -1.0, -1.0,
    ]);

    // itemSize = 3 because there are 3 values (components) per vertex
    geometry.setAttribute("position", new THREE.BufferAttribute(vertices, 3));

    const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });

    const rectangleMesh = new THREE.Mesh(geometry, material);
    scene.add(rectangleMesh);

    const controls = new OrbitControls(camera, renderer.domElement);
    camera.position.z = 5;
    controls.update();

    function animate() {
      requestAnimationFrame(animate);
      renderer.render(scene, camera);
    }
    animate();
  });
</script>

<div>
  <div>Mesh Rendering</div>
  <div id="canvas-container" />
</div>
