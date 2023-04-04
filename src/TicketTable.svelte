<script>
    export let tickets = [];
    let total = 0;
  
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
    }
  
    function calculateTotal() {
      total = tickets.reduce((acc, ticket) => acc + ticket.price, 0);
    }
  </script>
  
  <table>
    <thead>
      <tr>
        <th>Número</th>
        <th>Precio</th>
        <th>Acciones</th>
      </tr>
    </thead>
    <tbody>
      {#each tickets as ticket}
        <tr>
          <td>{ticket.id}</td>
          <td>
            <input type="number" step="any" value={ticket.price} on:change={() => handlePriceChange(ticket.id, event.target.value)} />
          </td>
          <td>
            <button on:click={() => handleDelete(ticket.id)}>Borrar</button>
          </td>
        </tr>
      {/each}
    </tbody>
    <tfoot>
      <tr>
        <th>Total:</th>
        <th>{total.toFixed(2)} €</th>
        <th></th>
      </tr>
    </tfoot>
  </table>