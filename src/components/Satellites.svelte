<!-- Satellites.svelte -->
<script>
    import { satelliteStore } from "../store.js";
    import Satellite from "./Satellite.svelte";
</script>

{#if $satelliteStore.length === 0}
    <p>Loading...</p>
{:else}
    <div class="satellite-container">
        {#each $satelliteStore as satellite}
            <Satellite {satellite} />
        {/each}
    </div>
{/if}

<!-- <style>
        .satellite-container {
            position: relative;
            width: 100%;
            height: 100%;
            /* overflow: auto; Scroll if content overflows */
            overflow-y: hidden; /* Scroll if content overflows vertically */
            overflow-x: hidden; /* Prevent horizontal scrolling */
        }
    </style> -->

<!-- <style>
        .satellite-container {
            position: relative;
            display: flex;
            flex-wrap: wrap;
            width: 100%;
            height: 100%;
            overflow-y: hidden; /* Allow vertical scrolling if content overflows */
            overflow-x: hidden; /* Prevent horizontal scrolling */
        }
    </style> -->

<style>
    .satellite-container {
        position: relative; /* Ensures that child elements with absolute positioning are positioned relative to this container */
        z-index: 2000;
        width: 100%;
        height: 100%; /* Ensures the container is as tall as the viewport */
        /* padding-bottom: 200px; Add padding to the container */
    }
</style>
