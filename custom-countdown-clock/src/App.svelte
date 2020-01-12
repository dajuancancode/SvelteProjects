<script>
	import {hours, minutes, seconds} from './util/options'
	let daysLeft;
	let hoursLeft;
	let minutesLeft;
	let secondsLeft;
	let chosenDate = '2020-01-14';
	let hour;
	let minute;
	let second;
	let countdown = '';

	$: time = `${hour}:${minute}:${second}`

	const beginCountdown = () => {
		const date 	= new Date(`${chosenDate}T${time}`).getTime()

		countdown = setInterval(() => {
			let now 			= new Date().getTime()
			let distance 	= Math.floor((date - now) / 1000)

			if (now >= date) {
				clearInterval(countdown)
				console.log('Done')
			}

			daysLeft 			= Math.floor(distance / 86400)
			hoursLeft 		= Math.floor(distance / 3600) % 24
			minutesLeft 	= Math.floor(distance / 60) % 60
			secondsLeft 	= distance % 60

			console.log(`${daysLeft}:${hoursLeft}:${minutesLeft}:${secondsLeft}`)
		}, 1000)

		
	}

</script>

<main>
	<form on:submit|preventDefault = {beginCountdown}>
		<label for="date">Date</label>
		<input type="date" bind:value="{chosenDate}" id = "date">
		<label for="hour">Hour</label>
		<select id = "hour" bind:value={hour}>
			{#each hours as hour}
				<option value = {hour.text}>
					{hour.text}
				</option>
			{/each}
		</select>
		<label for="minute">Minute</label>
		<select id ="minute" bind:value={minute}>
			{#each minutes as minute}
				<option value = {minute.text}>
					{minute.text}
				</option>
			{/each}
		</select>
		<label for="second">Seconds</label>
		<select id = "second" bind:value={second}>
			{#each seconds as second}
				<option value = {second.text}>
					{second.text}
				</option>
			{/each}
		</select>
		<input type="submit" value="Submit">
	</form>
</main>

<style>
	.form-item {
		display: flex;
	}
</style>