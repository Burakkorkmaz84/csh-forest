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
</script>
{#if data.length>0}
<div class="m-10">

  <div class="flex ">
    <div class="w-full" style="background-color:#172734;height: 600px;">
      <Canvas>
        <Scene {data} bind:selectedT={selectedT} bind:isPlaying={isPlaying} {steps} />
      </Canvas>

    </div>
    <!-- <div class="">
      {#if data.length>0}
        <Multiline {data} {selectedT} />
      {/if}
    </div> -->
  </div>
  
  <!-- <p>{$selectedId}</p> -->
  
  <div class="mt-10 flex justify-center">
    <button class="rounded-full p-2" on:click={()=>isPlaying=!isPlaying}>{@html isPlaying ? "⏸️":"▶️"}</button>
    <input type="range" min={145} max={steps[1]} style="width: 400px" bind:value={selectedT} class="slider" id="myRange">
    <span>{selectedT}</span>
  </div>
  <div class="flex flex-col">
    {#if lineData.length>0}
    <div class="felx justify-center">
      <Line data={lineData} options={{x: "t", y: "ravg_top"}} />
      
    </div>
    <div class="felx justify-center">
      <Line data={lineData} options={{x: "t", y: "ravg"}} />
    </div>
    <div class="felx justify-center">
      <Line data={lineData} options={{x: "t", y: "rsum"}} />
    </div>
    {/if}
  </div>
</div>
{:else}
<div>loading...</div>
{/if}
