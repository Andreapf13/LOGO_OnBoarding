
<script>
  import TicketForm from './TicketForm.svelte';
  import TicketTable from './TicketTable.svelte';

  let tickets = [];

  function handleAddTicket(event) {
    tickets = [...tickets, event.detail];
  }
</script>

<h1>FRUTERÍA ANDREA</h1>
<TicketForm on:addTicket={handleAddTicket} />
<TicketTable {tickets} />