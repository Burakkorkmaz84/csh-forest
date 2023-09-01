<script>
import { T } from '@threlte/core'
</script>


<T.Mesh receiveShadow position.y={-0.01} rotation.x={-90 * (Math.PI / 180)}>
    <!-- <T.PlaneGeometry args={[50, 50]} /> -->
    <T.CircleGeometry args={[30, 72]} />
    <T.MeshStandardMaterial color={"#3dbb9f"}  transparent opacity={0.8} />
</T.Mesh>