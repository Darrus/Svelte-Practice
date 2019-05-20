<script>
    import { createEventDispatcher } from "svelte";

    export let title;
    export let price;
    export let bestseller = false;

    const dispatch = createEventDispatcher();

    function addToCart() {
        dispatch('add-to-cart');
    }

    function deleteItem() {
        dispatch('delete-item');
    }
</script>

<article>
    <h1>{title}</h1>
    <h2>${price}</h2>
    <button on:click="{addToCart}">Add to Cart</button>
    <button on:click="{deleteItem}">Delete</button>
</article>