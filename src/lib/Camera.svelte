    <script>
    import { T } from '@threlte/core'
    import { OrbitControls } from '@threlte/extras';
    </script>



<T.PerspectiveCamera
    makeDefault
    position={[22, 15,22]}
    on:create={({ ref }) => {
        ref.lookAt(0, 0, 4);
}}>	
    <OrbitControls
        enableDamping
        target={[0, 4, 0]}
    />
</T.PerspectiveCamera>

<T.DirectionalLight castShadow position={[10, 20, 5]} >
    <T.PerspectiveCamera
    attach="shadow.camera"
    left={-100}
    right={100}
    top={100}
    bottom={-100}
    near={1}
    far={10000}
    />
    <T.Vector2 attach="shadow.mapSize" args={[4196, 4196]} />
</T.DirectionalLight>

