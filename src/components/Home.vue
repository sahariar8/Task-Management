<script setup>
import { ref } from "vue";

const newTask = ref("");
const tasks = ref([]);
const completedTask = ref([]);
const showCompletedTable = ref(false);

const taskAdd = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};
const taskDelete = (index) => {
  tasks.value.splice(index, 1);
};

const completeTask = (index, e) => {
  if (e.target.checked) {
    completedTask.value.push(tasks.value[index]);
    tasks.value.splice(index, 1);

  }
};

const completedTaskList = () => {
    showCompletedTable.value = !showCompletedTable.value;
}


</script>
<template>
  <div class="col-md-8 mx-auto border rounded-lg mt-8">
    <h1
      class="text-3xl font-bold p-2 bg-purple-800 rounded-lg text-center text-white"
    >
      Task Manager
    </h1>
    <h5 class="p-2 bg-purple-800 text-center text-green-500 mt-[-20px]">
      Create Your Daily Task
    </h5>

    <form class="mx-4" @submit.prevent="taskAdd">
      <div class="my-3">
        <input
          type="text"
          name="newTask"
          class="form-control"
          id="exampleInputEmail1"
          placeholder="Add your Task Here"
          v-model="newTask"
        />
      </div>
      <div class="flex justify-between">
        <button type="submit" class="btn btn-secondary">Add Task</button>
        <button type="submit" class="btn btn-success" @click="completedTaskList">Completed Task list</button>
      </div>
    </form>

    <div class="mt-5">
      <h1 class="text-3xl my-4 text-center font-bold text-emerald-700">
        Your Task List
      </h1>
      <table  v-if="!showCompletedTable"  class="table table-striped">
        <thead>
          <tr>
            <th>Status</th>
            <th>Serial</th>
            <th>Task</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(task, index) in tasks" :key="index">
            <td>
              <input
                type="checkbox" 
                name="radio" 
                @change="completeTask(index, $event)"
                v-model="completedTask"
              />
            </td>
            <td>{{ index + 1 }}.</td>
            <td class="w-[900px]">{{ task }}</td>
            <td>
              <button class="btn btn-warning">Edit</button>
              <button class="btn btn-error ml-1" @click="taskDelete(index)">
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
      <table  v-if="showCompletedTable"  class="table table-striped">
        <thead>
          <tr>
           
            <th>Serial</th>
            <th>Task</th>
            <th>Status</th>
           
          </tr>
        </thead>
        <tbody>
          <tr v-for="(task, index) in completedTask" :key="index">
            <td>{{ index + 1 }}.</td>
            <td class="w-[900px]">{{ task }}</td>
            <td>
                <button class="btn btn-success">Complete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
