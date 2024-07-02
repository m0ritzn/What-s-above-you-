<script>
    import { push } from "svelte-spa-router";

    function navigateToVisualisierung() {
        push("/visualisierung");
    }
</script>

<!-- Startbutton einfügen -->
<div class="landingpage">
    <h1>Willkommen bei What's above you?</h1>
    <p>
        What's above you? ist eine Webanwendung, die dir die aktuelle Position
        von Satelliten in Echtzeit anzeigt.
    </p>
    <p>
        Du kannst die Satelliten in einer Tabelle anzeigen lassen oder sie auf
        einer Weltkarte visualisieren.
    </p>
    <p>Wähle eine der beiden Optionen im Menü oben aus.</p>
    <button class="start-button" on:click={navigateToVisualisierung}
        >Start</button
    >
</div>

<style>
    .landingpage {
        display: flex;
        flex-direction: column;
        justify-content: center; /* Zentriert den Inhalt vertikal */
        align-items: flex-start; /* Ändert von left zu flex-start für korrekte Ausrichtung */
        height: 100vh;
        padding: 3em;
    }

    h1 {
        font-size: 2em;
        margin-bottom: 1em;
    }

    p {
        font-size: 1.25em;
        margin-bottom: 1em;
    }

    .start-button {
        padding: 1em 2em;
        font-size: 1.25em;
        color: white;
        background-color: #ffcc00;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    .start-button:hover {
        background-color: #deb100;
    }
</style>
