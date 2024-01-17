<script setup>
import { ref } from 'vue';
const tasks = ref([{
  name: 'Task 1',
  time: 30
}, {
  name: 'Task 2',
  time: 40
}, {
  name: 'Task 3',
  time: 60
}, {
  name: 'Task 4',
  time: 45
}, {
  name: 'Task 5',
  time: 50
}]);
// Delete task when click the delete button
function deleteTask(index) {
  tasks.value.splice(index, 1)
}

// Popup open 
let isPopupOpen = ref(false);


function addTask() {
  let taskName = document.querySelector('#taskname').value;
  let taskTime = document.querySelector('#tasktime').value;

  let newObj = {
    name: taskName,
    time: taskTime
  }

  tasks.value.push(newObj)
  document.querySelector('#taskname').value = ''
  document.querySelector('#tasktime').value = ''
  isPopupOpen = ref(false);
}


</script>
<template>
  <div class="container mx-auto my-4">
    <h2 class="text-center text-2xl">Task List Live test - Ostad</h2>
    <div v-for="(task, index) in tasks" :key="index"
      class="m-1 p-4 rounded bg-blue-300 flex items-center justify-between">
      <div>Task Name: {{ task.name }} <span>Time: {{ task.time }}</span></div>
      <button @click="deleteTask(index)"
        class="px-4 py-2 rounded bg-red-500 text-red-200 hover:bg-red-600">Delete</button>
    </div>
    <button @click="isPopupOpen = !isPopupOpen; console.log(isPopupOpen)"
      class="my-3 px-4 py-2 rounded bg-green-700 text-green-200">Add New Task</button>
    <div v-show="isPopupOpen">
      <label for="taskname">Enter Task Name</label><br>
      <input class="p-4 border border-blue-200" type="text" name="taskname" id="taskname"><br>
      <label for="tasktime">Enter Task Time</label><br>
      <input class="p-4 border border-blue-200" type="number" name="tasktime" id="tasktime"><br>
      <button @click="addTask()" class="my-3 px-4 py-2 rounded bg-green-400 bg-teal-100">Add Now</button>
    </div>
  </div>
</template>
<style></style>
