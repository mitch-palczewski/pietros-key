<script lang="ts">
    import {  useThrelte } from '@threlte/core';
    import { Environment, useTexture } from '@threlte/extras';
    import { EquirectangularReflectionMapping, SRGBColorSpace } from 'three';

    type Props = {
        path: string; 
        isBackground?: boolean; 
        intensity?: number; // 1. Add an intensity prop (1 is default full strength)
    };

    let { path, isBackground = true, intensity = 1 }: Props = $props();

    // svelte-ignore state_referenced_locally
    const textureStore = useTexture(path, {
        transform: (tex) => {
            tex.mapping = EquirectangularReflectionMapping;
            tex.colorSpace = SRGBColorSpace;
            return tex;
        }
    });

    let texture = $derived.by(() => $textureStore);

    // 2. Get access to the global Three.js scene object
    const { scene } = useThrelte();

    // 3. Reactively update the scene's environment intensity whenever the prop changes
    $effect(() => {
        scene.environmentIntensity = intensity;
    });
</script>

{#if texture}
    <Environment {texture} {isBackground} />
{/if}