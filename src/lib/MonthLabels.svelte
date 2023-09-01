<script>
	import { Text } from '@threlte/extras';

	export let d;
  export let x;
	export let z;
	export let y;

	const font = './Fonts/Raleway-Regular.ttf';
</script>

<Text
	text={d.month}
	position.x={x - 0.3}
	position.y={0.01}
	position.z={z + 3.5}
	color="#230612"
	fontSize={0.5}
	rotation.x={-Math.PI / 2}
	rotation.z={Math.PI / 2}
	fillOpacity={1}
	font={font}
	anchorX="center"
/>