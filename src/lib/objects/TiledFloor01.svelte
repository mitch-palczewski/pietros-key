<script lang="ts">
	import type { Position } from '$lib/types';
	import { T } from '@threlte/core';
	import type { Component } from 'svelte';

	type GridProvidedProps = {
        position: Position;
        size: number;
    };

	type Props<P extends GridProvidedProps> = {
        FloorTile: Component<P>;
        tileOptions?: Omit<P, keyof GridProvidedProps>; 
    };

	// eslint-disable-next-line @typescript-eslint/no-explicit-any
	let { FloorTile, tileOptions }: Props<any> = $props();

	const gridSize = 21;
	const spacing = 1;
	const blockSize = 3;

	let blocks: Array<{ id: string; position: Position }> = [];

	for (let x = 0; x < gridSize; x++) {
		for (let z = 0; z < gridSize; z++) {
			const posX = (x - (gridSize - 1) / 2) * blockSize * spacing;
			const posZ = (z - (gridSize - 1) / 2) * blockSize * spacing;

			blocks.push({
				id: `${x} + ${z}`,
				position: [posX, 0, posZ]
			});
		}
	}
</script>

<T.Group position={[0, -blockSize / 2, 0]}>
	{#each blocks as { id, position } (id)}
		<FloorTile {position} size={blockSize} {...tileOptions}/>
	{/each}
</T.Group>
