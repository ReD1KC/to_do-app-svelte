<script>
    import TaskItem from "./TaskItem.svelte";
  
    let tasks = []; 
    let showModal = false;
    let taskName = '';
    let date = '';
    let status = '';
  
    function addTask() {
      tasks = [
        ...tasks,
        { taskName, date, status },
      ];
      showModal = false;
      taskName = '';
      date = '';
      status = '';
    }
  
    function toggleModal() {
      showModal = !showModal;
    }
  </script>
  
  <main>
    <div class="table">
      {#each tasks as task}
        <TaskItem {task} date={task.date} status={task.status} taskName={task.taskName}/>
      {/each}
    </div>
    <button class="cnopka" on:click={toggleModal}>Добавить задачу</button>
  
    {#if showModal}
      <div class="modal">
        <form on:submit|preventDefault={addTask}>
          <label>Название задачи:</label>
          <input type="text" bind:value={taskName} />
          <label>Дата:</label>
          <input type="date" bind:value={date} />
          <button type="submit">Add Task</button>
        </form>
      </div>
    {/if}
  </main>
  
  <style>
    .table {
      display: flex;
      gap: 10px;
      flex-direction: column;
      border: 1px solid black;
      border-radius: 30px;
      padding: 5px;
    }
    .cnopka {
      margin-top: 10px;
      border: 1px solid black;
      border-radius: 30px;
      height: 30px;
      width: 200px;
    }
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .modal form {
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    }
  </style>