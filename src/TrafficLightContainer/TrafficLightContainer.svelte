<script>
    import Controls from './Controls/Controls.svelte';
    import TrafficLight from './TrafficLight/TrafficLight.svelte';

    let isRunning = false;
    let lights = {
        red: {
            id: 'red',
            class: ['light', 'red'],
            displayInSeconds: 8,
        },
        yellow: {
            id: 'yellow',
            class: ['light', 'yellow', 'off'],
            displayInSeconds: 3,
        },
        green: {
            id: 'green',
            class: ['light', 'green', 'off'],
            displayInSeconds: 5,
        },
    };

    function handleRun() {
        isRunning = !isRunning;
    }

    $: {
        console.log(isRunning, lights);
    }

</script>

<div class="traffic-light-container">
    <Controls 
        handleRun={handleRun} 
        lights={lights} 
        isRunning={isRunning} />
    <TrafficLight isRunning={isRunning} lights={lights} />
</div>

<style>
    .traffic-light-container {
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }
</style>