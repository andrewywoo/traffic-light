<script>
    export let toggleIsRunning;
    export let isRunning;
    export let lights;
</script>

<div class="controls">

    {#each Object.keys(lights) as light}
        <label for={light}>{light.charAt(0).toUpperCase() + light.slice(1)} Time (in seconds)</label>
        <input type="number" id={light} bind:value={lights[light].timeToDisplay}>
    {/each}
    <br>
    <button on:click={toggleIsRunning}>
        {#if isRunning} 
            Pause 
        {:else}
            Run
        {/if}
    </button>
</div>

<style>
    .controls {
        margin: 12px;
    }
</style>