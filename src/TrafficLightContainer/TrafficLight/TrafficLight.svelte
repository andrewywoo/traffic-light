<script>
    export let isRunning;
    export let lights;
    export let lightOrder;
    export let handleLightSwitch;
    import { onDestroy } from 'svelte';

    let seconds = 0;
    let currentLight = 0;
    $: interval = isRunning && setInterval(runTrafficLight, 1000)

    function runTrafficLight() {
        console.log(lights[lightOrder[currentLight]]);
        seconds += 1;
        if (seconds >= lights[lightOrder[currentLight]].timeToDisplay) {
            handleLightSwitch(lightOrder[currentLight]);
            currentLight === 2 ? currentLight = 0 : currentLight += 1;
            seconds = 0;
        }
    }

    onDestroy(() => clearInterval(interval));
</script>

<div class="traffic-light">
    {#each lightOrder as light}
        <div class={lights[light].class.join(' ')} />
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