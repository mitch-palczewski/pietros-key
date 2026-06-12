<script lang="ts">
	import Bull from "$lib/objects/Bull.svelte";
	import FloorTile01 from "$lib/objects/FloorTile01.svelte";
	import SceneEnvironment from "$lib/objects/SceneEnvironment.svelte";
	import TiledFloor01 from "$lib/objects/TiledFloor01.svelte";
	import { T } from "@threlte/core";

</script>

<T.PerspectiveCamera
  makeDefault
  position={[0, 5, -12]}
  oncreate={(ref) => {
    ref.lookAt(0, 1, 0)
  }}
/>
<T.DirectionalLight position={[10, 10, -10]} castShadow={true} />
<SceneEnvironment path='/sky.jpg' intensity={.4}/>
<TiledFloor01 FloorTile={FloorTile01}/>
<Bull/>