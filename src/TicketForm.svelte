<script>
    import { createEventDispatcher } from "svelte";
  
    const dispatch = createEventDispatcher();
  
    let price = "";
  </script>
  
  <form on:submit|preventDefault={() => dispatch("addTicket", { price })}>
    <label> Precio:
      <input type="number" bind:value={price} />
    </label>
  
    <button type="submit">Añadir ticket</button>
  </form>