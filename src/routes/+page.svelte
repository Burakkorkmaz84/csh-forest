<script>
    import { Canvas } from '@threlte/core'
    import Scene from './Scene.svelte'
    import Multiline from '$lib/Multiline.svelte';
    import { onMount } from 'svelte';
    import * as d3 from 'd3';
    import {selectedId} from '../stores/ui.js';
    import Line from '$lib/Line.svelte';

    let selectedT = 145;
    let isPlaying = false;
    let data = [];
    let lineData = []
    let steps = []

    async function load() {
      const data_file= "sim_grow_0_3_death_0_5.csv";
      
      const response = await fetch(data_file);
      if (response.ok) {
        const raw = d3.csvParse(await response.text(), d3.autoType);
        data = d3.merge(d3.flatGroup(raw,d=>d.id).map(([id,steps])=>(steps.map(s=>({...s, growT: s.t-d3.min(steps,d=>d.t)})))))
        steps = d3.extent(data, d=>d.t);
      }
      const lineRes = await fetch("sim_grow_0_3_death_0_5_agg.csv");
      lineData = d3.csvParse(await lineRes.text(), d3.autoType);

    }

		onMount(() => {
      load();
    });
    let audioEl;

    const togglePlay = () => {
      isPlaying=!isPlaying;
      isPlaying ? audioEl.play(): audioEl.pause()
    }
</script>
  <div class="m-10">
  <h1 class=" font-bold" style="font-size: 32px">Rhythm of the forest</h1>
  <p>Rhythm of the forest is an data visualization endowed with sonification based on the paper <strong>“Growth, death, and resource competition in sessile organisms” </strong>by Lee et al. to explore the dance of life, death, and competition among stationary creatures in nature.”
  </p>
  <div class="flex mt-8">
    <div class="w-full" style="background-color:#172734;height: 600px;">
      {#if data.length>0}
        <Canvas>
          <Scene {data} bind:selectedT={selectedT} bind:isPlaying={isPlaying} {steps} />
        </Canvas>
      {:else}
      <div class="text-white">loading...</div>
      {/if}
    </div>
    <!-- <div class="">
      {#if data.length>0}
        <Multiline {data} {selectedT} />
      {/if}
    </div> -->
  </div>
  
  <!-- <p>{$selectedId}</p> -->
  
  <div class="mt-10 flex justify-center">
    <button class="rounded-full p-2" on:click={togglePlay}>{@html isPlaying ? "⏸️":"▶️"}</button>
    <input type="range" min={145} max={steps[1]} style="width: 400px" bind:value={selectedT} class="slider" id="myRange">
    <span>{selectedT}</span>
  </div>
  <audio controls style="display: none" bind:this={audioEl}>
    <source src="audio.mp3" type="audio/mpeg">
  </audio>  
  <div>
    <p>
      The sonification consists of three layers corresponding to three parameters from the simulation: 
    </p>
    <ul>
      <li>
        - Average radius of the 10 biggest trees
      </li>
      <li>
        - Average radius of all trees
      </li>
      <li>
        - Sum of radii of all trees (to represent the fullness of the forest) 
      </li>
    </ul>
  </div>
  
  <div class="flex flex-col">
    {#if lineData.length>0}
    <div class="felx justify-center">
      <Line data={lineData} {selectedT} options={{x: "t", y: "ravg_top"}} />
      
    </div>
    <div class="felx justify-center">
      <Line data={lineData} {selectedT} options={{x: "t", y: "ravg"}} />
    </div>
    <div class="felx justify-center">
      <Line data={lineData} {selectedT} options={{x: "t", y: "rsum"}} />
    </div>
    {/if}
  </div>
</div>

