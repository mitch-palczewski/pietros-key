<script lang="ts">
	import type { Position } from '$lib/types';
	import type { Component } from 'svelte';

	type Props = {
		FloorTile: Component<{position: Position}>
	}

	let {FloorTile}: Props= $props()


	const gridSize = 21;
	const spacing = 1.1;
    const blockSize = 1

	let blocks: Array<{ id: string; position: Position}> = [];

	for (let x = 0; x < gridSize; x += blockSize) {
		for (let z = 0; z < gridSize; z += blockSize) {
			blocks.push({
				id: `${x} + ${z}`,
				position: [
                    (x - (gridSize -1) / 2) * spacing, 
                    0, 
                    (z -  (gridSize-1) / 2) * spacing
                ]
			});
		}
	}
</script>

{#each blocks as { id, position } (id)}
  <FloorTile position ={position}/>
{/each}
