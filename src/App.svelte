<script>
  import TicketForm from "./TicketForm.svelte";
  import TicketTable from "./TicketTable.svelte";

  let tickets = [];
  let total = 0;

  let nextId = 1;

  function addTicket(event) {
    const newTicket = {
      id: nextId,
      item: "",
      price: parseFloat(event.detail.price)
    };
    nextId++;
    tickets = [...tickets, newTicket];
    calculateTotal();
    if (tickets.length % 5 === 0) {
      alert(`¡Revisar caja! ${tickets.length} tickets añadidos`);
    }
  }

  function calculateTotal() {
    total = tickets.reduce((acc, ticket) => acc + ticket.price, 0);
  }
</script>

<h1>FRUTERÍA LOLA</h1>

<TicketForm on:addTicket={addTicket} />
<TicketTable bind:tickets={tickets} />

<h3>Total:</h3>
<h3>{total.toFixed(2)}</h3>