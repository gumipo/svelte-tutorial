<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();
  let name;
  let beltColor;
  let age;
  // let fighting = false;
  // let sneaking = false;
  // let running = false;

  const handleSubmit = () => {
    console.log(name, beltColor, age, skills);
    const person = {
      name,
      beltColor,
      age,
      skills,
      id: Math.floor(Math.random() * 100),
    };
    dispatch("addPerson", person);
  };

  let skills = [];
</script>

<style>
</style>

<!--
modifireがはいることでレンダリングをなくす -->
<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <input type="checkbox" bind:group={skills} value="fighting" />fighting<br />
  <input type="checkbox" bind:group={skills} value="sneaking" />sneaking<br />
  <input type="checkbox" bind:group={skills} value="running" />running<br />
  <label>Belt colour:</label>
  <select bind:value={beltColor}>
    <option value="balck">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>
  <button>Add Person</button>
</form>
