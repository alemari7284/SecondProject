<script>
  import Product from "./Product.svelte";
  import Modal from "./Modal.svelte";

  const products = [
    {
      id: "p1",
      title: "A book",
      price: 9.99,
    },
  ];

  let showModal = false;
  let closeable = false;
</script>

{#each products as prod}
  <Product
    {...prod}
    on:add-to-cart={(x) => {
      alert("Add to cart");
      console.log(x.detail);
    }}
    on:delete={(x) => {
      alert("Delete");
      console.log(x.detail);
    }}
  />
{/each}

<button on:click={() => (showModal = true)}>Show Modal</button>

{#if showModal}
  <Modal
    on:cancel={() => (showModal = false)}
    on:close={() => (showModal = false)}
    let:didAgree={closeable}
  >
    <h1 slot="header">Hello bitch!</h1>
    <p>scemo di merda</p>
    <button
      slot="footer"
      on:click={() => (showModal = false)}
      disabled={!closeable}>Confirm</button
    >
  </Modal>
{/if}
