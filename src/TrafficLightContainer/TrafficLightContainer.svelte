<script>
    import Controls from './Controls/Controls.svelte';
    import TrafficLight from './TrafficLight/TrafficLight.svelte';

    let isRunning = false;
    let lights = {
        red: {
            class: ['red'],
            timeToDisplay: 8,
        },
        yellow: {
            class: ['yellow', 'off'],
            timeToDisplay: 3,
        },
        green: {
            class: ['green', 'off'],
            timeToDisplay: 5,
        },
    };
    let lightOrder = Object.keys(lights);

    function toggleIsRunning() {
        isRunning = !isRunning;
    }

    function handleLightSwitch(currentLightIndex) {
        // Adds 'off' class to current light
        const currentLight = lightOrder[currentLightIndex];
        lights[currentLight].class = [...lights[currentLight].class, 'off'];

        // Increments current index to find next light index
        let nextLightIndex = currentLightIndex + 1;
        if (nextLightIndex > 2) {
            nextLightIndex = 0;
        }

        // Reassigns class name without 'off' class
        const nextLight = lightOrder[nextLightIndex];
        lights[nextLight].class = [lightOrder[nextLightIndex]];
    }

</script>

<div class="traffic-light-container">
    <Controls toggleIsRunning={toggleIsRunning} lights={lights} isRunning={isRunning} />
    <TrafficLight isRunning={isRunning} lights={lights} lightOrder={lightOrder} handleLightSwitch={handleLightSwitch} />
</div>

<style>
    .traffic-light-container {
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }
</style>