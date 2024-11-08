<script>
    import svelteLogo from "./assets/svelte.svg";
    import viteLogo from "/vite.svg";
    import Counter from "./lib/Counter.svelte";
    import TaskList from "./components/TaskList.svelte";
    import Filter from "./components/Filter.svelte";
</script>

<main>
    <div class="container">
        <h1>Трекер задач</h1>
    </div>
    <div class="tasklist">
        !!!
        <Filter/>
        <TaskList/>
    </div>
</main>

<style>
    .container {
        text-align: center;
    }

    .tasklist {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        padding-top: 30px;
    }
</style>
