<script>
    export let taskName;
    export let date;
    export let status;
    export let description;

    let showDescription = false;
</script>

<main>
    <div class="task">
        <div class="name">{taskName}</div>
        <div class="date">{date}</div>
        <div class="status">{status}</div>
        <button on:click={() => (showDescription = !showDescription)}
            >{showDescription ? "Скрыть" : "Показать описание"}
        </button>
        {#if showDescription}
            <div class="description">{description}</div>
        {/if}
    </div>
</main>

<style>
    .task {
        display: flex;
        flex-direction: column;
        border: 1px solid black;
        padding: 10px;
        text-align: center;
    }
    .description {
        padding: 10px;
        background-color: #f0f0f0;
        border: 1px solid #ccc;
        margin-top: 10px;
    }
</style>
