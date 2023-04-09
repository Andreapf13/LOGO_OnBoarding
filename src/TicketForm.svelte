<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    let price = "";

    function handleSubmit() {
        const ticket = {
            price: parseFloat(price),
            id: Math.floor(Math.random() * 1000),
        };

        dispatch("addTicket", ticket);
        price = "";
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <label> Precio:
        <input type="number" bind:value={price} />
    </label>

    <button type="submit">Añadir ticket</button>
</form>
