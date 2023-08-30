<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    font-family: Arial, sans-serif;
  }

  .container {
    text-align: center;
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	margin: auto;
  }

  input, button {
    margin: 5px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  ul {
    list-style: none;
    padding: 0;
  }

  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 5px 0;
    padding: 8px;
    background-color: #f5f5f5;
    border-radius: 4px;
  }

  button {
    background-color: #ff6347;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
</style>

<script>
  let tasks = [
    { id: 1, text: 'Buy groceries' },
    { id: 2, text: 'Finish Svelte project' },
    { id: 3, text: 'Call friend' }
  ];

  let newTask = '';

  function addTask() {
    if (newTask.trim()) {
      tasks = [...tasks, { id: Date.now(), text: newTask }];
      newTask = '';
    }
  }

  function removeTask(id) {
    tasks = tasks.filter(task => task.id !== id);
  }
</script>

<div class="container">
  <h2>Task List</h2>
  <input type="text" bind:value={newTask} placeholder="Enter a new task" />
  <button on:click={addTask}>Add Task</button>

  <ul>
    {#each tasks as task}
      <li key={task.id}>
        {task.text}
        <button on:click={() => removeTask(task.id)}>Delete</button>
      </li>
    {/each}
  </ul>
</div>
