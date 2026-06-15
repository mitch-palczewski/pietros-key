<script lang="ts">
	import TestScene01 from "$lib/scenes/TestScene01.svelte";
	import { Canvas } from "@threlte/core";
</script>

<div class="relative block w-screen h-screen overflow-hidden bg-black">
    <Canvas>
        <TestScene01/>
    </Canvas>
</div>