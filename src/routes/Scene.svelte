<script>
  	import { T } from '@threlte/core'
	import * as d3 from 'd3';

	import Bar from '../lib/Bar.svelte'
	import Floor from '../lib/Floor.svelte'
	import Camera from '../lib/Camera.svelte'
	import Light from '../lib/Light.svelte'
	import MonthLabels from '../lib/MonthLabels.svelte'
	import YearLabels from '../lib/YearLabels.svelte'
	import Title from '../lib/Title.svelte'
	import BarAnnotations from '../lib/BarAnnotations.svelte'
	import Grid from '../lib/Grid.svelte'
	import Cone from '$lib/Cone.svelte';

	
	export let selectedT;
	export let isPlaying;
	export let data = [];

	export let steps;
    // async function load() {
    //     const data_file= "https://raw.githubusercontent.com/stefanpullen/TutorialData/main/heathrow.csv";
    //     const response = await fetch(data_file);
    //     if(response.ok) {
    //         data = d3.csvParse(await response.text(), d3.autoType);
	// 					datafiltered = data.filter(d => d.year == 2011)
	// 					years = [...new Set(data.map(d => d.year))]
    //     }
    // }
	// async function load() {
	// 	const data_file= "growth.csv";
	// 	const response = await fetch(data_file);
	// 	if(response.ok) {
	// 		data = d3.csvParse(await response.text(), d3.autoType);
	// 	}
    // }

	setInterval(function () {
		if (isPlaying && selectedT<steps[1]) {
			selectedT++
		}
	}, 1000);	

    $: dataFiltered  = data.filter(d=> d.t == selectedT);

	$: xScale = d3
          .scaleLinear()
          .domain(d3.extent(data.map((d) => d.x)))
          .range([-20, 20]);
  
	$: yScale = d3
		.scaleLinear()
		.domain(d3.extent(data.map((d) => d.growT)))
		.range([0, 20]);

	$: zScale = d3
		.scaleLinear()
		.domain(d3.extent(data.map((d) => d.y)))
		.range([-20,20]);

	$: rScale = d3.scaleLinear()
				.domain(d3.extent(data.map(d=>d.r)))
				.range([0,10]);

</script>

<!-- <Title /> -->
<Floor />
<Camera/>
<!-- <Light/> -->

{#each dataFiltered as d}
    <Cone
		{d}
		{selectedT}
		step={d.t}
		r={rScale(d.r)}
        x={xScale(d.x)}
        y={yScale(d.growT)}
        z={zScale(d.y)}
		color={'#A8DF8E'}
    />
{/each}


<!-- 
{#each datafiltered as d} 
	<MonthLabels {d} 
					x={xScale(d.month)}
					y={yScale(d.rain)}
					z={zScale(d.year)}/>
{/each}

{#each years as d, i}
	<YearLabels {d}
	 				x={9}
					y={0.01}
					z={0 + 2*i}/>
{/each} -->
