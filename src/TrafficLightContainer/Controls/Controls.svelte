<script>
    export let handleRun;
    export let lights;
    export let isRunning;
    const { red, yellow, green } = lights;
</script>

<div class="controls">
    <label for="red">Red Timer (seconds):</label>
    <input type="number" id="red" bind:value={red.timeToDisplay} />
    <label for="yellow">Yellow Timer (seconds):</label>
    <input type="number" id="yellow" bind:value={yellow.timeToDisplay} />
    <label for="green">Green Timer (seconds):</label>
    <input type="number" id="green" bind:value={green.timeToDisplay} />
    <br>
    <button on:click={handleRun}>
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