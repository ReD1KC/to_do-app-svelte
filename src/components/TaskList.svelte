<script>
    import { onMount } from "svelte";
    import TaskItem from "./TaskItem.svelte";

    let tasks = [];
    let showModal = false;
    let taskName = "";
    let date = "";
    let status = "";
    let statusOptions = ["Надо сделать", "В процессе", "Сделанно"];
    let taskDescription = "";

    onMount(() => {
        const storedTasks = localStorage.getItem("tasks");
        if (storedTasks) {
            tasks = JSON.parse(storedTasks);
        }
    });

    function addTask() {
        tasks = [...tasks, { taskName, date, status, taskDescription }];
        localStorage.setItem("tasks", JSON.stringify(tasks));
        showModal = false;
        taskName = "";
        date = "";
        status = "";
        taskDescription = "";
    }

    function deleteTask(index) {
        tasks = tasks.filter((_, i) => i !== index);
        localStorage.setItem("tasks", JSON.stringify(tasks));
    }

    function toggleModal() {
        showModal = !showModal;
    }

    function closeModal() {
        showModal = false;
    }
</script>

<main>
    <div class="table">
        {#each tasks as task, index}
            <TaskItem
                date={task.date}
                status={task.status}
                taskName={task.taskName}
                description={task.taskDescription}
            />
            <button on:click={() => deleteTask(index)}>Удалить</button>
        {/each}
    </div>
    <button class="cnopka" on:click={toggleModal}>Добавить задачу</button>

    {#if showModal}
        <div class="modal">
            <form on:submit|preventDefault={addTask}>
                <label>Название задачи:</label>
                <input type="text" bind:value={taskName} required />
                <label>Дата:</label>
                <input type="date" bind:value={date} required />
                <label>Статус:</label>
                <select bind:value={status} required>
                    {#each statusOptions as option}
                        <option value={option}>{option}</option>
                    {/each}
                </select>
                <label>
                    Описание:<label>
                        <textarea bind:value={taskDescription} required
                        ></textarea>
                        <button type="submit">Добавить задачу</button>
                    </label></label
                >
            </form>
        </div>
    {/if}
</main>

<style>
    .table {
        display: flex;
        flex-direction: column;
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
