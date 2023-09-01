<script>
  import { Canvas } from '@threlte/core'
  import Scene from './Scene.svelte'
    let selectedT = 1;
</script>

<div class="">
    <p>current time: {selectedT}</p>
    <input type="range" min="1" max="199" bind:value={selectedT} class="slider" id="myRange">
</div>

<div class="canvas-wrapper">
  <Canvas>
    <Scene bind:selectedT={selectedT} />
  </Canvas>
</div>



<style>
  .canvas-wrapper {
    width: 100%;
    height: 600px;
  }

  .radio-inputs {
      z-index:1
  }
</style>