<script>
    import { push } from "svelte-spa-router";
    import { onMount } from "svelte";

    let menuOpen = false;

    function navigateTo(path) {
        push(path);
        menuOpen = false; // Schließt das Menü nach der Navigation
    }

    function toggleMenu() {
        menuOpen = !menuOpen;
    }

    onMount(() => {
        const handleResize = () => {
            if (window.innerWidth > 768) {
                menuOpen = false;
            }
        };

        window.addEventListener("resize", handleResize);

        return () => {
            window.removeEventListener("resize", handleResize);
        };
    });
</script>

<nav class="navbar">
    <div class="logo">
        <a
            href="/"
            on:click={(e) => {
                e.preventDefault();
                navigateTo("/");
            }}>What's above you?</a
        >
    </div>
    <div class="hamburger" on:click={toggleMenu}>&#9776;</div>
    <div class={`nav-links ${menuOpen ? "open" : ""}`}>
        <a
            class="nav-link"
            href="#"
            on:click={(e) => {
                e.preventDefault();
                navigateTo("/visualisierung");
            }}>Visualisierung</a
        >
        <a
            class="nav-link"
            href="#"
            on:click={(e) => {
                e.preventDefault();
                navigateTo("/tabelle");
            }}>Tabelle</a
        >
    </div>
</nav>

<style>
    .navbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 2.5em 3em;
        position: relative; /* Wichtig für die absolute Positionierung der Menüpunkte */
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

    .hamburger {
        display: none;
        font-size: 30px;
        cursor: pointer;
    }

    @media (max-width: 768px) {
        .nav-links {
            display: none;
            flex-direction: column;
            position: absolute;
            top: 150px; /* Positioniert die Menüpunkte direkt unter der Navbar */
            right: 0;
            background-color: #02001a;
            width: 100%;
            padding: 1em 0;
            z-index: 1000; /* Stellt sicher, dass die Menüpunkte über anderen Elementen liegen */
        }

        .nav-links.open {
            display: flex;
        }

        .hamburger {
            display: block;
        }

        .nav-link {
            margin: 1em 0;
            text-align: center;
        }
    }
</style>
