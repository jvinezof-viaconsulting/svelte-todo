<script>
  import { toDoItems } from "./store.js";
  import { onMount } from "svelte";

  export let userName;
  let newItem = "";
  let newItemInputForm = null;

  onMount(() => {
      newItemInputForm.focus();
  })

  function addToDoList() {
    $toDoItems = [...$toDoItems, { text: newItem, status: false }];
    newItem = "";
  }
</script>

<form on:submit|preventDefault={addToDoList}>
    <input bind:value={newItem} bind:this={newItemInputForm} type="text" placeholder="Add new task" />
    <button type="submit">Add</button>
</form>

<h3>{userName}'s task list:</h3>
