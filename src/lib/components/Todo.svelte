<script>
    import { onMount } from 'svelte';
    import toast, { Toaster } from 'svelte-french-toast';
  
    let tasks = [];
    let newTask = '';
    let isInputValid = false;
  
    onMount(() => {
      const storedTasks = localStorage.getItem('tasks');
      if (storedTasks) {
        tasks = JSON.parse(storedTasks);
      }
    });
  
    function addTask() {
      if (newTask.trim() && tasks.length < 20) {
        tasks = [...tasks, newTask.trim()];
        localStorage.setItem('tasks', JSON.stringify(tasks));
        newTask = '';
        toast.success('Task added successfully!');
      } else if (tasks.length >= 20) {
        toast.error('Maximum number of tasks reached!');
      } else {
        toast.error('Please enter a valid task!');
      }
    }
  
    function removeTask() {
      if (tasks.length > 0) {
        tasks = tasks.slice(0, -1);
        localStorage.setItem('tasks', JSON.stringify(tasks));
        toast.success('Last task removed!');
      } else {
        toast.error('No tasks to remove!');
      }
    }
  
    function validateInput() {
      isInputValid = newTask.trim().length > 0;
    }
  </script>
  
  <main class="container mx-auto p-4 max-w-md">
    <h1 class="text-2xl font-bold mb-4 text-center">Todo List</h1>
  
    <div class="form-control">
      <label class="label" for="task-input">
        <span class="label-text">New Task</span>
      </label>
      <div class="input-group">
        <input
          type="text"
          id="task-input"
          placeholder="Enter a task"
          class="input input-bordered flex-grow"
          bind:value={newTask}
          on:input={validateInput}
        />
        <button
          class="btn btn-primary"
          on:click={addTask}
          disabled={!isInputValid || tasks.length >= 20}
        >
          Add Task
        </button>
      </div>
    </div>
  
    <button
      class="btn btn-secondary mt-4 w-full"
      on:click={removeTask}
      disabled={tasks.length === 0}
    >
      Remove Last Task
    </button>
  
    <ul class="mt-4 space-y-2">
      {#each tasks as task, index}
        <li class="bg-base-200 p-2 rounded">
          {index + 1}. {task}
        </li>
      {/each}
    </ul>
  
    <p class="mt-4 text-sm">
      Tasks: {tasks.length} / 20
    </p>
  </main>