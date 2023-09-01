<script>
	import { Text } from '@threlte/extras';

	export let d;
  export let x;
	export let z;
	export let y;

	const font1 = './Fonts/BonaNova-Regular.ttf';
	const font2 = './Fonts/Raleway-Regular.ttf';
</script>

<Text
	text={d.rain}
	position.x={x - 0.3}
	position.y={y + 0.01}
	position.z={z}
	color="#230612"
	fontSize={0.4}
	rotation.x={-Math.PI / 2}
	rotation.z={Math.PI / 2}
	fillOpacity={1}
	font={font2}
	anchorX="center"
/>


