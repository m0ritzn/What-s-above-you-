<script>
    export let satellite;

    // Maximum altitude for scaling purposes (you can adjust this based on your data)
    const maxAltitude = 35000; // example maximum altitude in kilometers
    let top = 100 - (satellite.satalt / maxAltitude) * 100 + "%"; // Inverse because CSS top starts from the top
    let left = Math.random() * 90 + "%"; // Keep random left positioning
</script>

<div class="dot" style="top: {top}; left: {left};">
    <div class="tooltip">
        <h3>{satellite.satname}</h3>
        <div class="info-group">
            <p><span>ID:</span> <span>{satellite.satid}</span></p>
            <p>
                <span>intDesignator:</span>
                <span>{satellite.intDesignator}</span>
            </p>
        </div>
        <h5>Position</h5>
        <div class="info-group">
            <p><span>Launch Date:</span> <span>{satellite.launchDate}</span></p>
            <p><span>Altitude:</span> <span>{satellite.satalt} km</span></p>
            <p><span>Latitude:</span> <span>{satellite.satlat}</span></p>
            <p><span>Longitude:</span> <span>{satellite.satlng}</span></p>
        </div>
    </div>
</div>

<style>
    .dot {
        height: 50px;
        width: 50px;
        background-image: url("../assets/satellite.png");
        background-size: cover;
        position: absolute;
        animation: float 3s infinite ease-in-out alternate;
        z-index: 1;
        transition: all 0.25s ease;
        cursor: pointer;
    }

    @keyframes float {
        0% {
            transform: translate(0, 0);
        }
        100% {
            transform: translate(10px, -10px);
        }
    }

    .tooltip {
        visibility: hidden;
        display: inline-block;
        justify-content: center;
        align-items: center;
        margin: 0;
        background-color: #f5f5f5;
        color: black;
        border-radius: 10px;
        padding: 20px;
        box-shadow: 0px 0px 10px rgb(255, 255, 255);
        width: 200px;
        position: absolute; /* Position tooltip relative to .dot */
        transition: transform all 0.3s ease;
        bottom: 100%;
        z-index: 2000; /* Ensure tooltip is on top of other elements */
    }

    .info-group {
        margin-top: 10px;
    }

    .tooltip h3 {
        margin: 0;
        font-size: 22px;
    }

    .tooltip h5 {
        margin-top: 10px;
        font-size: 18px;
        margin-bottom: 10px;
    }

    .tooltip .info-group p {
        margin: 5px 0;
        display: flex;
        justify-content: space-between;
    }
    .dot:hover {
        width: 60px;
        height: 60px;
    }
    .dot:hover .tooltip {
        visibility: visible;
        opacity: 1;
    }
</style>
