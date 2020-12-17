<script>
  export let isPromo = false;
  export let showModal = false;
</script>

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }
  .promo .modal {
    background: pink;
  }
</style>

{#if showModal}
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <!-- <slot name="title"   具体的に受け取ることもできる/>
      <p>hey there...</p> -->
      <slot />
    </div>
  </div>
{/if}
