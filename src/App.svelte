<script>
	// import Card from './Card.svelte';
	import TrafficLightContainer from './TrafficLightContainer/TrafficLightContainer.svelte';
</script>

<main>
	<!-- <div style="display: flex;">
		<Card name="Andrew" occupation="Software Engineer" age={31} color="blue" />
		<Card name="Kathleen" occupation="Nurse" age={30} color="green" />
		<Card name="Cameron" occupation="Accountant" age={28} color="blue" />
	</div> -->
	<TrafficLightContainer />

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
</style>