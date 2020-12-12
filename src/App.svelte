<script>
	let firstName = "ねこ";
	let lastName = "ひろし";
	let beltColor = "red";

	$: fullName = `${firstName}${lastName}`;

	$: {
		console.log(fullName);
	}

	const handleClick = () => {
		beltColor = "blue";
	};

	//bind:valueで使わない
	// const handleInput = (e) => {
	// 	name = e.target.value;
	// };
</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1 style="color:{beltColor}">{fullName}</h1>
	<button on:click={handleClick}>update-color</button>
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName} />
</main>
