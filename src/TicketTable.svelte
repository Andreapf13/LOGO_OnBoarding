<script>

    export let tickets = [];

    function handleDelete(id) {
        tickets = tickets.filter((ticket) => ticket.id !== id);
        calculateTotal();
    }

    function handlePriceChange(id, price) {
        tickets = tickets.map((ticket) => {
            if (ticket.id === id) {
                ticket.price = parseFloat(price);
            }
            return ticket;
        });
        calculateTotal();
      
    }

   
</script>

{#each tickets as ticket}
    <p>ID TICKET: {ticket.id}</p>
    <input
        type="number"
        value={ticket.price}
        on:change={() => handlePriceChange(ticket.id, event.target.value)}
    />
    <button on:click={() => handleDelete(ticket.id)}>Borrar</button>
{/each}
