<script>



	let daysLeft;
	let hoursLeft;
	let minutesLeft;
	let secondsLeft;
	

	const beginCountdown = () => {
		const date 						= new Date(`${month} ${day}, ${year} ${hour}:${minute}:${second}`).valueOf()
		const now 						= Date.now().valueOf()
		let secondDifference 	= Math.floor((date - now) / 1000)

		setInterval(() => {
			daysLeft 							= Math.floor(secondDifference / 86400)
			hoursLeft 						= Math.floor(secondDifference / 3600) % 24
			minutesLeft 					= Math.floor(secondDifference / 60) % 60
			secondsLeft 					= secondDifference % 60
			secondDifference -= 1
	}, 1000)
	}
</script>

<main>
	
</main>

<style>
	
</style>