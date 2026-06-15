<script lang="ts">
	import type { Position } from '$lib/types';
	import { T } from '@threlte/core';

    type Props = {
        position: Position;
		size: number;
		edgeWidth: number
    }
	let {position = 0, size=1, edgeWidth = .1}: Props = $props();


	const mainColor = "#bdb395"
	const edgeColor = '#bd954f'
	const castShadow = false 
	const receiveShadow = true

	const edgeHeight = .8
	// svelte-ignore state_referenced_locally
	const mainWidth = 1 - (edgeWidth*2)
	// svelte-ignore state_referenced_locally
	const edgePosOffest = .5 - (edgeWidth/2)

</script>

<T.Group position={position} scale={[size,1,size]}>
	<T.Mesh {castShadow} {receiveShadow}>
		<T.BoxGeometry args={[mainWidth, 1, mainWidth]} />
		<T.MeshStandardMaterial color={mainColor} />
	</T.Mesh>

	<T.Mesh {castShadow} {receiveShadow} position={[edgePosOffest,0,0]}>
		<T.BoxGeometry args={[edgeWidth, edgeHeight, mainWidth]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
	<T.Mesh {castShadow} {receiveShadow} position={[- edgePosOffest,0,0]}>
		<T.BoxGeometry args={[edgeWidth, edgeHeight, mainWidth]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>

	<T.Mesh {castShadow} {receiveShadow} position={[0,0,edgePosOffest]}>
		<T.BoxGeometry args={[mainWidth, edgeHeight, edgeWidth]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
	<T.Mesh {castShadow} {receiveShadow} position={[0,0, - edgePosOffest]}>
		<T.BoxGeometry args={[mainWidth, edgeHeight, edgeWidth]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
</T.Group>
