<script lang="ts">
    import * as PIXI from "pixi.js";
    import { onMount } from "svelte";
    let canvas: HTMLCanvasElement;
    let width = 800;
    let height = 500;
    onMount(() => {
        const app = new PIXI.Application();
        app.init({
            canvas: canvas,
            width: width,
            height: height,
            backgroundColor: 0x000000,
            resolution: window.devicePixelRatio,
        });
    });
</script>

<canvas
    bind:this={canvas}
    {width}
    {height}
    style="width: {width}px; height: {height}px;"
></canvas>
