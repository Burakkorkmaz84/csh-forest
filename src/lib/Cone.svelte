<script>
    import { T } from '@threlte/core';
    import { interactivity, Text } from '@threlte/extras'
	import { spring } from 'svelte/motion'

    interactivity()
	export let selectedT;
    export let step;
	export let x;
	export let z;
	export let y;
	export let color;
	export let r;

//   const sizeR = spring(r);
//   const sizeY = spring(y);
//   const hover = spring(0)

// $: if (step === selectedT) {
// 	sizeR.set(r)
// }
// $: selectedT, sizeR.set(r);
// $: selectedT, sizeY.set(y);
</script>
    <T.Mesh
          position.x={x}
          position.z={z}
		  position.y={y/2}
		  rotation.x={-180 * (Math.PI / 180)}  
            receiveShadow>
     <!-- <T.BoxGeometry /> -->
	 <T.ConeGeometry args={[r, y, 64]} />
     <T.MeshStandardMaterial color={'#A8DF8E'}  opacity= {0.8}
	 transparent ={true} />
    </T.Mesh>