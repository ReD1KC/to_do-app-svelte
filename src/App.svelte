<script>
    import svelteLogo from "./assets/svelte.svg";
    import viteLogo from "/vite.svg";
    import Counter from "./lib/Counter.svelte";
    import TaskList from "./components/TaskList.svelte";
</script>

<main>
    <div class="container">
        <h1>Трекер задач</h1>
    </div>
    <div class="tasklist">
        !!!
        <TaskList/>
    </div>
</main>

<style>
    .container {
        text-align: center;
    }

    .tasklist {
        text-align: center;
        padding-top: 30px;
    }
</style>
