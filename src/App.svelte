<script>
  import Navbar from "./components/Navbar.svelte";
  import SpaceObjects from "./components/SpaceObjects.svelte";
  import { satelliteStore } from "./store.js";
  import Satellites from "./components/Satellites.svelte";
  import PlanetWorld from "./components/PlanetWorld.svelte";
  import Table from "./components/Table.svelte";

  import Router from "svelte-spa-router";
  import Visualisierung from "./components/Visualisierung.svelte";
  import LandingPage from "./components/LandingPage.svelte";

  // // Daten hier aus API Laden
  $: console.log($satelliteStore);

  const routes = {
    "/": LandingPage,
    "/visualisierung": Visualisierung,
    "/tabelle": Table,
  };
</script>

<!-- alles in rouer verlagern -->
<SpaceObjects />
<main>
  <Navbar />
  <Router {routes} />
</main>

<style>
  :global(*) {
    /* background-color: transparent; */
    /* color: white; */
  }
  main {
    /* padding: 2em; */
    display: flex;
    flex-direction: column;
    margin: 0;
    font-family: Arial, sans-serif;
    background-image: url("../src/assets/Sternenhimmel\ Francesco\ Ungaro.jpg"); /* Replace with the path to your image */
    background-size: cover; /* Adjust the background size to cover the entire container */
    background-repeat: no-repeat; /* Prevent the background from repeating */
    background-position: center; /* Center the background image */
    color: white;
    height: 100vh; /* Full viewport height */
  }
</style>
