<script>
    export let isRunning;
    export let lights;
</script>

<div class="traffic-light">
    {#each Object.keys(lights) as light}
        <div id={lights[light].id} class={lights[light].class.join(' ')} />
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