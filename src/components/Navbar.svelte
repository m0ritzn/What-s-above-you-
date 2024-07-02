<script>
    import { push } from "svelte-spa-router";

    function navigateTo(path) {
        push(path);
    }
</script>

<nav class="navbar">
    <div class="logo">
        <a href="/" on:click={() => navigateTo("/")}>What's above you?</a>
    </div>
    <div class="nav-links">
        <a
            class="nav-link"
            href="javascript:void(0);"
            on:click={() => navigateTo("/visualisierung")}>Visualisierung</a
        >
        <a
            class="nav-link"
            href="javascript:void(0);"
            on:click={() => navigateTo("/tabelle")}>Tabelle</a
        >
    </div>
</nav>

<style>
    .navbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 2.5em 3em;
    }

    .logo a {
        font-size: 42px; /* Einheit px hinzugefügt */
        font-weight: bold;
        color: white; /* Textfarbe hinzugefügt */
        text-decoration: none; /* Entfernt die Unterstreichung */
        transition: color 0.3s;
        cursor: pointer;
    }

    .nav-links {
        display: flex;
    }

    .nav-link {
        margin-left: 2em;
        color: white;
        text-decoration: none;
        font-size: 1em;
        transition: color 0.3s;
        cursor: pointer;
    }

    .nav-link:hover,
    .logo a:hover {
        color: #ffcc00;
    }
</style>
