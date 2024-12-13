<script setup>
    const value = 
</script>

<template>
    <div>
        <h1 class="text-3xl font-bold p-2 bg-purple-800 text-center text-white">Task Manager</h1>
        <h5 class=" p-2 bg-purple-800 text-center text-green-500 mt-[-20px]">Create Your Daily Task</h5>

        <form class="mx-4" >
            <div class="my-3">
                <input type="text" name="task" class="form-control" id="exampleInputEmail1" placeholder="Add your Task Here">
            </div>
            <button type="submit" class="btn btn-success">Add Task</button>
        </form>
    </div>
</template>