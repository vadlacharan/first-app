<script>
    import { prevent_default } from "svelte/internal";

	let todos = []
	let todo = 
	{
		task:"", iscomplete:false
	}

	function HandleAddTask(e)
	{
		
		todos = [...todos,{...todo}]
		todo.task = ""
	}

	function HandleClear()
	{
		todos = []
	}

	
</script>

<main>
	<h1>TODO APP</h1>
	<form on:submit|preventDefault={HandleAddTask}>
		<input type="text" id="task" bind:value={todo.task} autocomplete="off">
	<button id="addtask">Add Task</button>
	<button id="clear" on:click={HandleClear}>clear</button>
	</form>
	
	

	<h1>YOUR TASKS</h1>

	<ul class="list-group">
		{#each todos as todo }
			{#if todo.task == ""}
			{:else}			  
				<li class="list-group-item" class:completed={todo.iscomplete}>{todo.task}<span><input type="checkbox" id="iscomplete" bind:checked={todo.iscomplete}></span></li>
			{/if}
		{:else}
			<p>No Tasks </p>
		{/each}

	</ul>

</main>

<style>

	.completed
	{
		text-decoration: line-through;
	}
	
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>