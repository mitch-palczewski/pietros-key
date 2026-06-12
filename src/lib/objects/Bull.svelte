<script lang="ts">
    import ImageCharacter from './ImageCharacter.svelte';
	import CharacterAnimator from './CharacterAnimator.svelte';
</script>


{#snippet bullSnippet()}
    <ImageCharacter texturePath="/creatures/Bull.png" size={3}/>
{/snippet}

<CharacterAnimator character={bullSnippet}/>