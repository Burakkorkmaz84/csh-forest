<script>
	import { T } from '@threlte/core';
  import { interactivity, Text } from '@threlte/extras'
	import { spring } from 'svelte/motion'

  interactivity()
	export let selectedYear;
	export let year;
	export let x;
	export let z;
	export let y;
	export let color;
	export let rain

  const height = spring(y)
	const hover = spring(0)

$: if (year === selectedYear ) {
	height.set(y)
}
else if (selectedYear == 'all') {
		height.set(y)
}
else {
		height.set(0.01)
}
</script>



<T.Mesh
	position.x={x}
	position.y={($height /2) + $hover }
	position.z={z}
	scale.y={$height}
  castShadow
  receiveShadow
	on:pointerenter={() => year == selectedYear ? hover.set(1) : null}
  on:pointerleave={() => year == selectedYear ? hover.set(0) : null}

>
	<T.BoxGeometry />
	<T.MeshStandardMaterial {color} />
</T.Mesh>

<Text
	text={rain + " ml"}
	position.x={x}
	position.y={($height + $hover ) +1.8}
	position.z={z}
	color="#230612"
	fontSize={0.8}
	fillOpacity={$hover}
	anchorX="center"
/>