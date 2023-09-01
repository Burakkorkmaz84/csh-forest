<script>
	import { Text } from '@threlte/extras';

	export let d;
  export let x;
	export let z;
	export let y;

	const font = './Fonts/Raleway-Regular.ttf';
</script>

<Text
	text={d}
	position.x={x}
	position.y={y}
	position.z={z}
	color="#230612"
	fontSize={0.6}
	rotation.x={-Math.PI / 2}
	rotation.z={Math.PI / 2}
	fillOpacity={1}
	font={font}
	anchorX="center"
/>