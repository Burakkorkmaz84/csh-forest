<script>
  import { Canvas } from '@threlte/core'
  import Scene from './Scene.svelte'
    let selectedT = 1;
    let isPlaying = false;
</script>

<div class="canvas-wrapper">
  <Canvas>
    <Scene bind:selectedT={selectedT} bind:isPlaying={isPlaying} />
  </Canvas>
</div>

<div class="mt-10 flex justify-center">
  <button class="rounded-full p-2" on:click={()=>isPlaying=!isPlaying}>{@html isPlaying ? "⏸️":"▶️"}</button>
  <input type="range" min="1" max="199" style="width: 400px" bind:value={selectedT} class="slider" id="myRange">
  <span>{selectedT}</span>
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