<script>
</script>

<div class="planet-container">
    <div class="earth"></div>
</div>

<style>
    .planet-container {
        position: relative;
        width: 100%;
        /* height: 100%; */
        /* height: 25vh; */
        height: 30%;
        z-index: 1;
        /* padding-top: 100px; */
    }

    .earth {
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 100%;
        height: 100%;
        background-color: transparent;
        background-image: url("../assets/erde.png");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: top;
        z-index: 0;
    }
</style>
