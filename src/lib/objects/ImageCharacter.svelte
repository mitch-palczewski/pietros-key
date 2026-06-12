<script lang="ts">
    import { T, type Props } from '@threlte/core';
    import { useTexture } from '@threlte/extras';
    import { DoubleSide, Group } from 'three';
    
    type ComponentProps = Props<Group>&{
        texturePath: string;
        size?: number;
        castShadow?: boolean;
        receiveShadow?: boolean;
    }

    let { 
        texturePath,
        size = 1, 
        castShadow = true,
        receiveShadow = false,
        ...restProps 
    }: ComponentProps = $props();

    // svelte-ignore state_referenced_locally
    const textureStore = useTexture(texturePath);
    let texture = $derived.by(() => $textureStore);
    
    let dimensions = $derived.by(() => {
        if (!texture || !texture.image) return { width: 0, height: 0 };
        const aspectRatio = texture.image.width / texture.image.height;
        return { width: size, height: size / aspectRatio };
    });
</script>

<T.Group {...restProps}>
  {#if dimensions.width > 0 && texture}
    <T.Mesh position.y={dimensions.height / 2} {castShadow} {receiveShadow}>
      <T.PlaneGeometry args={[dimensions.width, dimensions.height]} />
      <T.MeshStandardMaterial 
        map={texture} 
        transparent={true} 
        side={DoubleSide} 
        alphaTest={0.5}
      />
    </T.Mesh>
  {/if}
</T.Group>