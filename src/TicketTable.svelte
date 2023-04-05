<script>
    import { createEventDispatcher } from 'svelte';
  
    const dispatch = createEventDispatcher();
  
    export let tickets = [];
    export let total = 0;
  
    function handleDelete(id) {
      tickets = tickets.filter(ticket => ticket.id !== id);
      calculateTotal();
    }
  
    function handlePriceChange(id, price) {
      tickets = tickets.map(ticket => {
        if (ticket.id === id) {
          ticket.price = parseFloat(price);
        }
        return ticket;
      });
      calculateTotal();
      dispatch('priceChange', { tickets, total });
    }
  
    function calculateTotal() {
      total = tickets.reduce((acc, ticket) => acc + ticket.price, 0);
    }
  </script>
  
  
      {#each tickets as ticket}
    
          <p>ID TICKET: {ticket.id}</p>
            <input type="number"  value={ticket.price} on:change={() => handlePriceChange(ticket.id, event.target.value)} />
            <button on:click={() => handleDelete(ticket.id)}>Borrar</button>
       
      {/each}
 
        <h3>Total:</h3>
        <h3>{total.toFixed(2)} €</h3>

      

  