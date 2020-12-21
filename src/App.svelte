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

	const addPerson = (e) => {
		// console.log(e.detail);
		const person = e.detail;
		people = [person, ...people];
		console.log(people);
		showModal = false;
	};
</script>

<!-- {#if num > 20}
	<p>gereater ehan 20</p>
{:else if num > 5}
	<p>gereter ehan 5</p>
{:else}
	<p>not greter</p>
{/if} -->

<Modal message="propsを渡すよー" {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson} />
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
