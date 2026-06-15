<script lang="ts">
    import ImageCharacter from './ImageCharacter.svelte';
	import CharacterAnimator from './CharacterAnimator.svelte';
	import { T, type Props } from '@threlte/core';
	import type { Group } from 'three';

    type ComponentProps = Props<Group>

    let {     
        ...restProps 
    }: ComponentProps = $props();
</script>


{#snippet bullSnippet()}
    <ImageCharacter texturePath="/creatures/Table-Lion-Girl.png" size={3}/>
{/snippet}


<T.Group {...restProps}>
    <CharacterAnimator character={bullSnippet}/>
</T.Group>
