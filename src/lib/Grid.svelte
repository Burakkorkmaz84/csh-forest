<script>
import { T } from '@threlte/core';
import { Text } from '@threlte/extras';
export let y;

const font2 = './Fonts/Raleway-Regular.ttf';
</script>


<T.Mesh
 position.x={9}
 position.y={y/2}
 position.z={-1}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 1, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-11}
 position.y={y/2}
 position.z={-1}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 1, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-11}
 position.y={y/2}
 position.z={5}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 1, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-11}
 position.y={y/2}
 position.z={2}
 rotation.x={-90 * (Math.PI / 180)}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 1.1, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-11}
 position.y={y}
 position.z={2}
 rotation.x={-90 * (Math.PI / 180)}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 1.1, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-1}
 position.y={y}
 position.z={-1}
 rotation.x={-90 * (Math.PI / 180)}
 rotation.z={-90 * (Math.PI / 180)}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 3.7, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<T.Mesh
 position.x={-1}
 position.y={y/2}
 position.z={-1}
 rotation.x={-90 * (Math.PI / 180)}
 rotation.z={-90 * (Math.PI / 180)}
 scale.y={y}
  castShadow
receiveShadow
 >
  <T.BoxGeometry args={[0.1, 3.7, 0.1]}/>
  <T.MeshBasicMaterial color="black" />
</T.Mesh>



<Text
	text={"120mm"}
	position.x={9.2}
	position.y={y + 0.3}
	position.z={-1}
	color="#230612"
	fontSize={0.4}
	
	fillOpacity={1}
	font={font2}
	anchorX="left"
/>

