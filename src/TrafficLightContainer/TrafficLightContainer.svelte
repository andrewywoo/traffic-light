<script>
    import Controls from './Controls/Controls.svelte';
    import TrafficLight from './TrafficLight/TrafficLight.svelte';

    let isRunning = false;
    let lights = {
        red: {
            class: ['light', 'red'],
            timeToDisplay: 8,
        },
        yellow: {
            class: ['light', 'yellow', 'off'],
            timeToDisplay: 3,
        },
        green: {
            class: ['light', 'green', 'off'],
            timeToDisplay: 5,
        },
    };
    let lightOrder = Object.keys(lights);

    function handleRun() {
        isRunning = !isRunning;
    }

    function handleLightSwitch(currentLight) {
        lights[currentLight].class = [...lights[currentLight].class, 'off'];
        const nextLightIndex = (lightOrder.indexOf(currentLight) + 1) > 2 ? 0 : lightOrder.indexOf(currentLight) + 1;
        lights[lightOrder[nextLightIndex]].class = ['light', lightOrder[nextLightIndex]];
    }

</script>

<div class="traffic-light-container">
    <Controls handleRun={handleRun} lights={lights} isRunning={isRunning} />
    <TrafficLight isRunning={isRunning} lights={lights} lightOrder={lightOrder} handleLightSwitch={handleLightSwitch} />
</div>

<style>
    .traffic-light-container {
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }
</style>