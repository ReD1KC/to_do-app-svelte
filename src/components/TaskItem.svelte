<script>
    export let taskName;
    export let date;
    export let status;
    export let onDelete;

    function handleDelete() {
        onDelete();
    }
</script>

<main>
    <div class="task">
        <div class="name">{taskName}</div>
        <div class="date">{date}</div>
        <div class="status">{status}</div>
    </div>
</main>

<style>
    .task {
        display: flex;
        flex-direction: column;
        border: 1px solid black;
        border-radius: 30px;
        padding: 10px;
        text-align: center;
    }
</style>
