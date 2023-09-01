<script>
import { T } from '@threlte/core'
</script>


<T.Mesh receiveShadow position.y={-0.01} rotation.x={-90 * (Math.PI / 180)}>
    <T.CircleGeometry args={[80, 72]} />
    <T.MeshStandardMaterial color={"#854d0e"}  transparent opacity={0.8} />
</T.Mesh>