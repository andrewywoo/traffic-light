<script>
    export let name;
    export let occupation;
    export let age;
    export let color;
    
    let classNames = ['card'];
    $: fill = `fill-${color}`;
    $: isFilled = classNames.includes(fill);

    function selectBox() {
        if (isFilled) {
            classNames = ['card'];
        } else {
            classNames = [...classNames, fill];
        }
    }
</script>

<div class={classNames.join(' ')} on:click={selectBox}>
    <h1 class={isFilled && fill}>{name}</h1>
    <h2 class={isFilled && fill}>{occupation}</h2>
    <p class={isFilled && fill}>{age} years old</p>
</div>

<style>
    .card {
        display: flex;
        flex-flow: column;
        justify-content: center;
        align-items: center;
        height: 300px;
        width: 300px;
        border: 1px solid black;
        margin: 12px;
    }

    .fill-green {
        background-color: green;
        color: white;
    }

    .fill-blue {
        background-color: blue;
        color: white;
    }
</style>