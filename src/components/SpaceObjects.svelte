<script>
    import { onMount, onDestroy } from "svelte";
    import { satelliteStore } from "../store.js";

    let data;
    let intervalId;

    async function fetchData() {
        try {
            const response = await fetch(
                // `/api/rest/v1/satellite/above/48/9/0/10/0/&apiKey=${import.meta.env.VITE_API_KEY}`,
                `/api/rest/v1/satellite/above/48/9/0/10/{category_id}/&apiKey=${import.meta.env.VITE_API_KEY}`,
            );
            if (!response.ok) {
                throw new Error(`HTTP error! Status: ${response.status}`);
            }
            data = await response.json();
            satelliteStore.set(data.above || []); // Save the data in the store
            console.log(data); // Print the data to the console
        } catch (error) {
            console.error("Error fetching data:", error);
        }
    }

    onMount(() => {
        fetchData();
        // Set the interval to fetch data every 5 minutes (300000 milliseconds)
        intervalId = setInterval(fetchData, 10000);
    });

    onDestroy(() => {
        clearInterval(intervalId); // Clear the interval when the component is destroyed
    });

    // import { onMount } from "svelte";
    // import { satelliteStore } from "../store.js";

    // let data;

    // async function fetchData() {
    //     try {
    //         const response = await fetch(
    //             // `/api/rest/v1/satellite/above/48/9/0/10/0/&apiKey=${import.meta.env.VITE_API_KEY}`,
    //             `/api/rest/v1/satellite/above/48/9/0/10/{category_id}/&apiKey=${import.meta.env.VITE_API_KEY}`,
    //         );
    //         if (!response.ok) {
    //             throw new Error(`HTTP error! Status: ${response.status}`);
    //         }
    //         data = await response.json();
    //         satelliteStore.set(data.above || []); // Save the data in the store
    //         console.log(data); // Print the data to the console
    //     } catch (error) {
    //         console.error("Error fetching data:", error);
    //     }
    // }

    // onMount(() => {
    //     fetchData();
    // });

    // -----------------------------------------

    // let data = [];
    // const categories = {
    //     1: "Amateurfunk",
    //     2: "Kommunikation",
    //     3: "Wetter",
    //     // Weitere Kategorien hinzufügen
    // };

    // async function fetchDataForCategory(categoryId) {
    //     const response = await fetch(
    //         `/api/rest/v1/satellite/above/48/9/0/10/${categoryId}/&apiKey=${import.meta.env.VITE_API_KEY}`,
    //     );
    //     if (!response.ok) {
    //         throw new Error(`HTTP-Fehler! Status: ${response.status}`);
    //     }
    //     const result = await response.json();
    //     return result.above || [];
    // }

    // async function fetchData() {
    //     try {
    //         const promises = Object.keys(categories).map(async (categoryId) => {
    //             const satellites = await fetchDataForCategory(categoryId);
    //             return satellites.map((satellite) => ({
    //                 ...satellite,
    //                 category: categories[categoryId],
    //             }));
    //         });

    //         const results = await Promise.all(promises);
    //         data = results.flat();
    //         satelliteStore.set(data); // Speichert die Daten im Store
    //         console.log(data); // Gibt die Daten in der Konsole aus
    //     } catch (error) {
    //         console.error("Fehler beim Abrufen der Daten:", error);
    //     }
    // }

    // onMount(() => {
    //     fetchData();
    // });
</script>
