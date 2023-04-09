<script>
  import TicketForm from "./TicketForm.svelte";
  import TicketTable from "./TicketTable.svelte";

let tickets = [];
let total = 0;


function handleAddTicket(event) {
  tickets = [...tickets, event.detail];
}

function handlePriceChange(event) {
  const { id, price } = event.detail;
  tickets = tickets.map((ticket) => {
    if (ticket.id === id) {
      ticket.price = price;
    }
    return ticket;
  });
}

$: total = tickets.reduce((acc, ticket) => acc + ticket.price, 0);
$: if (tickets.length % 5 === 0) {
    alert(`¡Revisar caja! ${tickets.length} tickets añadidos`);
  }

</script>

<h1>FRUTERÍA LOLA</h1>

<TicketForm on:addTicket={handleAddTicket} />
<TicketTable on:priceChange={handlePriceChange} {tickets} {total} />

<h3>Total:</h3>
<h3>{total.toFixed(2)} </h3>
