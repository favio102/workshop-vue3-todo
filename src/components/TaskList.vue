<script setup>
  import TaskCard from "@/components/TaskCard.vue";
  import { reactive,ref } from "vue";

  const tasks = reactive([])
    // {
    //   title: "Create a card component",
    //   description:
    //     "Create a new TaskCard.vue file in the components folder, then import it in TasksList",
    //   done: true,
    // },
    // {
    //   title: "Make the card component dynamic",
    //   description:
    //     "Learn about using the data option and passing data to child components using props",
    //   done: true,
    // },
    // {
    //   title: "Bind the attributes to the data",
    //   description:
    //     "Use the v-bind directive to bind the title and description to our data",
    //   done: false,
    // }
    function addTask(title, description) {
      tasks.unshift({ title, description });
    }
    function resetForm() {
      newTitle.value = ""
      newDescription.value = ""
      // hide the form
      showNewTaskForm.value = false
    }
    const newTitle = ref("")
    const newDescription = ref("")
    const showNewTaskForm = ref(false)
</script>

<template>
  <button class="btn round-icon" @click="showNewTaskForm = !showNewTaskForm">＋</button>
  <div v-show="showNewTaskForm" class="task-card new-task" v-on:keyup.enter="addTask(newTitle, newDescription), resetForm()">
    <div>
      <input type="text" placeholder="What would you like to do?" v-model="newTitle"/>
      <textarea placeholder="Add some details about your task..." v-model="newDescription"></textarea>
    </div>
  </div>
  <TaskCard v-if="tasks.length > 0" v-for="(task, index) in tasks" v-bind:title="task.title" :description="task.description" :done="task.done" />
  <p v-else>You do not have tasks...</p>
</template>

<style lang="scss" scoped>
@keyframes expand-vertical { from { min-height: 0; height: 0; } to { min-height: 6rem; } }
.task-card.new-task {
  animation: expand-vertical 0.2s;
  overflow: hidden;
  background-color: white;
  border-left: solid 5px #35495e;
  &, &:hover { transform: scale(1.1); box-shadow: 2px 3px 10px rgba(black, 0.2); }
  & + .tasks-list { pointer-events: none; }
  input { font-size: 1.17rem; font-weight: bold; width: 100%; }
  textarea { width: 100%; font-size: 0.9rem; resize: none; }
}
</style>
