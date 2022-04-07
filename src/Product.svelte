<script>
  import { createEventDispatcher } from "svelte"
  
  export let title;
  export let price;
  export let bestseller = true;
  const dispatch = createEventDispatcher();

  const addToCart = () => {
    dispatch('add-to-cart', {id: 'p1'});  
  }
</script>

<article>
  <h1>{title}</h1>
  <h1>${price}</h1>
  {#if bestseller}
    <h2>BESTSELLER</h2>
  {/if}
  <button on:click={addToCart}>Add to cart</button>
  <button on:click={() => dispatch('delete', {id: 'p2'})}>Delete</button>
</article>
