<script>
  let name;
  let beltColor;
  let age;
</script>

<style>
</style>

<form>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="text" placeholder="beltColor" bind:value={beltColor} />
  <input type="number" bind:value={age} />
  <button>Add Person</button>
</form>
