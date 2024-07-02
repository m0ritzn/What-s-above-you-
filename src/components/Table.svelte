<script>
    import { satelliteStore } from "../store.js";
    import { writable, get } from "svelte/store";

    let sortedSatellites = writable([]);
    let sortKey = writable("");
    let sortDirection = writable("asc");

    function sortSatellites() {
        const key = get(sortKey);
        const direction = get(sortDirection);
        const satellites = get(satelliteStore);

        if (!key) {
            sortedSatellites.set(satellites);
            return;
        }

        sortedSatellites.set(
            [...satellites].sort((a, b) => {
                let aKey = a[key];
                let bKey = b[key];
                if (typeof aKey === "string") aKey = aKey.toLowerCase();
                if (typeof bKey === "string") bKey = bKey.toLowerCase();

                if (aKey < bKey) return direction === "asc" ? -1 : 1;
                if (aKey > bKey) return direction === "asc" ? 1 : -1;
                return 0;
            }),
        );
    }

    function handleSort(key) {
        if (get(sortKey) === key) {
            sortDirection.update((direction) =>
                direction === "asc" ? "desc" : "asc",
            );
        } else {
            sortKey.set(key);
            sortDirection.set("asc");
        }
        sortSatellites();
    }

    // Automatically sort and update the table whenever satelliteStore changes
    // $: {
    //     sortSatellites(get(satelliteStore));
    // }

    $: {
        if (get(satelliteStore).length > 0) {
            sortSatellites();
        }
    }
</script>

{#if $satelliteStore.length === 0}
    <p>Loading...</p>
{:else}
    <div class="table-container">
        <table class="styled-table">
            <thead>
                <tr>
                    <th on:click={() => handleSort("satname")}>Name</th>
                    <th on:click={() => handleSort("intDesignator")}
                        >Int. Designator</th
                    >
                    <th on:click={() => handleSort("satid")}>ID</th>
                    <th on:click={() => handleSort("launchDate")}
                        >Launch Date</th
                    >
                    <th on:click={() => handleSort("satalt")}>Altitude</th>
                    <th on:click={() => handleSort("satlat")}>Latitude</th>
                    <th on:click={() => handleSort("satlng")}>Longitude</th>
                </tr>
            </thead>
            <tbody>
                {#each $sortedSatellites as satellite}
                    <tr>
                        <td>{satellite.satname}</td>
                        <td>{satellite.intDesignator}</td>
                        <td>{satellite.satid}</td>
                        <td>{satellite.launchDate}</td>
                        <td>{satellite.satalt} km</td>
                        <td>{satellite.satlat}</td>
                        <td>{satellite.satlng}</td>
                    </tr>
                {/each}
            </tbody>
        </table>
    </div>
{/if}

<style>
    .table-container {
        padding: 0 3em; /* Adds padding to left and right */
        margin: 20px 0;
    }

    .styled-table {
        width: 100%;
        border-collapse: collapse;
    }

    th,
    td {
        border: 1px solid white;
        padding: 8px;
        text-align: left;
    }

    th {
        background-color: #2e3d59;
        cursor: pointer;
    }

    tr {
        background-color: #141a26;
    }

    tr:nth-child(even) {
        background-color: #1e2b43;
    }
</style>
