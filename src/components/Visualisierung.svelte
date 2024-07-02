<script>
    import SpaceObjects from "./SpaceObjects.svelte";
    import Satellites from "./Satellites.svelte";
    import PlanetWorld from "./PlanetWorld.svelte";
    import Router from "svelte-spa-router";
</script>

<!-- <SpaceObjects /> -->
<div class="visualisation">
    <Satellites />
    <PlanetWorld />
</div>

<style>
    .visualisation {
        display: flex;
        flex-direction: column; /* Change to column for vertical stacking */
        height: 100%; /* Full viewport height */
    }

    .visualisation > * {
        flex: 1;
        position: relative;
    }
</style>
