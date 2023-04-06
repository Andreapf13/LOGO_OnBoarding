<script>
    import TicketForm from './TicketForm.svelte';
    import TicketTable from './TicketTable.svelte';
    
    let tickets = [];
    let total = 0;
    
    function handleAddTicket(event) {
        tickets = [...tickets, event.detail];
    }

    $: if (tickets.length && (tickets.length % 5) === 0) {
        alert(`¡Revisar caja! 5 tickets añadidos. El total debería ser ${total.toFixed(2)} €`);
    }
    
    $: total = tickets.reduce((acc, ticket) => acc + ticket.price, 0);
</script>

<h1>FRUTERÍA ANDREA</h1>
<TicketForm on:addTicket={handleAddTicket} />
<TicketTable bind:tickets={tickets} />

<h3>Total:</h3>
<h3>{total.toFixed(2)} €</h3>
