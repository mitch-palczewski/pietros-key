<script lang="ts">
	import type { Position } from '$lib/types';
	import { T } from '@threlte/core';

    type Props = {
        position: Position
    }

	const mainColor = "#bdb395"
	const edgeColor = '#bd954f'
	const castShadow = false 
	const receiveShadow = true

    let {position = 0}: Props = $props();
</script>

<T.Group position={position}>
	<T.Mesh {castShadow} {receiveShadow}>
		<T.BoxGeometry args={[0.8, 1, 0.8]} />
		<T.MeshStandardMaterial color={mainColor} />
	</T.Mesh>

	<T.Mesh {castShadow} {receiveShadow} position={[.45,0,0]}>
		<T.BoxGeometry args={[0.1, .95, .8]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
	<T.Mesh {castShadow} {receiveShadow} position={[-.45,0,0]}>
		<T.BoxGeometry args={[0.1, .95, .8]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>

	<T.Mesh {castShadow} {receiveShadow} position={[0,0,.45]}>
		<T.BoxGeometry args={[.8, .95, .1]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
	<T.Mesh {castShadow} {receiveShadow} position={[0,0, -.45]}>
		<T.BoxGeometry args={[.8, .95, .1]} />
		<T.MeshStandardMaterial color={edgeColor} />
	</T.Mesh>
</T.Group>
