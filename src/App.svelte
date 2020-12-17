<script>
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";

	let showModal = false;

	let people = [
		{ name: "neko", beltColor: "black", age: 25, id: 1 },
		{ name: "inu", beltColor: "orange", age: 34, id: 2 },
		{ name: "ushi", beltColor: "pink", age: 17, id: 3 },
	];

	const handleClick = (id) => {
		people = people.filter((person) => person.id != id);
	};

	let num = 4;

	const toggleModal = () => {
		showModal = !showModal;
	};
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

<!-- {#if num > 20}
	<p>gereater ehan 20</p>
{:else if num > 5}
	<p>gereter ehan 5</p>
{:else}
	<p>not greter</p>
{/if} -->

<Modal {showModal} on:click={toggleModal} isPromo={true}>
	<AddPersonForm />
</Modal>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.name === 'neko'}
				<p>こいつは猫ちゃんだーーー</p>
			{/if}
			<p>{person.age}歳 , {person.beltColor}</p>
			<button on:click={() => handleClick(person.id)}>delete</button>
		</div>
	{:else}
		<p>peopleないよーーー</p>
	{/each}
</main>
