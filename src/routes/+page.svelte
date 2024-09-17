<script>
    // @ts-nocheck
    
        let todoName = '';
        let todoDate = '';
        let todoDescription = '';
        let tasks = [];
    
        function addTask(event) {
            event.preventDefault();
            if (todoName && todoDate && todoDescription) {
                tasks = [...tasks, {
                    name: todoName,
                    date: todoDate,
                    description: todoDescription
                }];
                todoName = '';
                todoDate = '';
                todoDescription = '';
            }
        }
    
        function clearTasks() {
            tasks = [];
        }
    </script>
    
    <head>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
    <div class="flex flex-col md:flex-row items-center justify-center py-10 space-y-8 md:space-y-0 md:space-x-8 bg-default bg-cover h-[100vh]">
        <div class="w-full h-[80%] max-w-md p-6 bg-white rounded-lg shadow-md">
            <h1 class="text-2xl font-bold mb-6 text-center">Enter To-Do's</h1>
            <form on:submit={addTask} class="space-y-4">
                <div class="form-group">
                    <label for="todo-name" class="block text-sm font-medium text-gray-700">To-Do Name</label>
                    <input type="text" id="todo-name" bind:value={todoName} class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Enter task name" required>
                </div>
                <div class="form-group">
                    <label for="todo-date" class="block text-sm font-medium text-gray-700">Date</label>
                    <input type="date" id="todo-date" bind:value={todoDate} class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" required>
                </div>
                <div class="form-group">
                    <label for="todo-description" class="block text-sm font-medium text-gray-700">Description</label>
                    <textarea id="todo-description" bind:value={todoDescription} class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Enter task description"></textarea>
                </div>
                <button type="submit" class="w-full bg-blue-500 text-white py-2 px-4 rounded-md hover:bg-blue-600">Add To-Do</button>
            </form>
        </div>
    
        <div class="w-full h-[80%] max-w-md p-6 bg-white rounded-lg shadow-md overflow-y-auto">
            <h2 class="text-xl font-bold mb-6 text-center">My To-Do's</h2>
            {#if tasks.length > 0}
                <ul class="space-y-2">
                    {#each tasks as task (task.name)}
                        <li class="p-4 bg-gray-100 rounded-md shadow-sm">
                            <strong>{task.name}</strong> - {task.date}<br>
                            <span class="text-sm">{task.description}</span>
                        </li>
                    {/each}
                </ul>
                <button on:click={clearTasks} class="w-full mt-4 bg-red-500 text-white py-2 px-4 rounded-md hover:bg-red-600">Clear All Tasks</button>
            {:else}
                <p class="text-center text-gray-500">No tasks added yet.</p>
            {/if}
        </div>
    </div>
    </body>
    
    <style>
        body {
            font-family: serif;
        }
    </style>
    