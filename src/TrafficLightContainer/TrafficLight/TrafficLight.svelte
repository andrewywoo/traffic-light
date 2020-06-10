<script>
    export let isRunning;
    export let lights;
    export let lightOrder;
    export let handleLightSwitch;
    import { onDestroy, beforeUpdate, afterUpdate } from 'svelte';

    let seconds = 0;
    let currentLightIndex = 0;
    let interval;

    beforeUpdate(() => {
        clearInterval(interval);
    });

    afterUpdate(() => {
        interval = isRunning && setInterval(runTrafficLight, 1000);
    });

    function runTrafficLight() {
        seconds += 1;
        
        const currentLight = lightOrder[currentLightIndex];
        const timeToDisplayCurrentLight = lights[currentLight].timeToDisplay;

        if (seconds >= timeToDisplayCurrentLight) {
            handleLightSwitch(currentLightIndex);

            // Move to next light index after switching lights.
            currentLightIndex === 2 ? currentLightIndex = 0 : currentLightIndex += 1;
            seconds = 0;
        }
    }

    onDestroy(() => clearInterval(interval));
</script>

<div class="traffic-light">
    {#each lightOrder as light}
        <div class={[...lights[light].class, 'light'].join(' ')} />
    {/each}
</div>

<style>
    .traffic-light {
        border: 1px solid black;
        height: 150px;
        width: 80px;
        display: flex;
        flex-flow: column;
        align-items: center;
        justify-content: center;
        background-color: GoldenRod;
        margin: 12px;
        margin-top: 28px;
    }

    .light {
        height: 30px;
        width: 30px;
        border: 1px solid black;
        border-radius: 25px;
        margin: 6px;
    }

    .red {
        background-color: red;
    }

    .yellow {
        background-color: yellow;
    }

    .green {
        background-color: green;
    }

    .off {
        background-color: black !important;
    }
</style>