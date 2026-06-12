<script lang="ts">
    import { T, useTask } from '@threlte/core';
	import type {  Snippet } from 'svelte';

    type Props = {
        character: Snippet
    }
    let {character}: Props = $props()

    let positionX = $state(0);
    let time = $state(0)

    const speed = .7;     
    const distance = 4;  

    useTask((delta) => {
        time += delta
        positionX = Math.sin(time * speed) * distance;
    });
</script>

<T.Group position.x={positionX}>
    {@render character()}
</T.Group>