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

let isPopupOpen = ref(false)

let runningIndex = ref(undefined)


// update task
function updateTask(ind){
  let updateTaskName = document.querySelector('#taskname').value;
  let updateTaskTime = document.querySelector('#tasktime').value;
  let updateTask = {
    name: updateTaskName,
    time: updateTaskTime
  }
  tasks.value.splice(ind,1,updateTask)
  document.querySelector('#taskname').value = '';
  document.querySelector('#tasktime').value = '';
  isPopupOpen = ref(false)
}

</script>
<template>
  
  <div class="container mx-auto my-4">
    <!-- for finding index -->
    <h2 class="text-xl runningId hidden" v-bind="runningIndex">{{ runningIndex }}</h2>
    <h2 class="text-center text-2xl">Task List Live test - Ostad</h2>
    <div v-for="(task, index) in tasks" :key="index"
      class="m-1 p-4 rounded bg-blue-300 flex items-center justify-between">
      <div>Task Name: {{ task.name }} <span>Time: {{ task.time }}</span></div>
      <button @click="isPopupOpen = !isPopupOpen;runningIndex = index"  class="px-4 py-2 rounded bg-teal-500 text-teal-200 hover:bg-teal-600">Edit</button>
    </div>


    <!-- button for submit -->
    <button @click="updateTask(runningIndex)" class="my-3 px-4 py-2 rounded bg-green-700 text-green-200">Submit</button>



    <div v-show="isPopupOpen">
      <label for="taskname">Enter Task Name</label><br>
      <input class="p-4 border border-blue-200" type="text" name="taskname" id="taskname"><br>
      <label for="tasktime">Enter Task Time</label><br>
      <input class="p-4 border border-blue-200" type="number" name="tasktime" id="tasktime"><br>
    </div>


  </div>
</template>
<style></style>
