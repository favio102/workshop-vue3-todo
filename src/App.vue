<script setup>
  import TaskList from '@/components/TaskList.vue';
</script>

<template>
  <header>
    <img alt="Vue logo" src="./assets/logo.svg" height="100" />
    <h1>Task Manager</h1>
  </header>

  <main>
      <TaskList />
  </main>

</template>


<style lang="scss" scoped>
header {
  text-align: center;
  color: #5b91c6;
  margin: auto;
  margin-top: 60px;
  min-height: 20vh;
}

main {
  text-align: center;
  color: #7295b7;
  margin: auto;
  padding: 3em 0 3em 0;
  max-width: 600px;
  min-height: 50vh;
}

footer {
  text-align: center;
  margin: 2em 0;
  font-size: 0.8em;
  color: #aaa;
}

.logos svg {
  margin: 0.8em;
  fill: #aaa;

  &:hover {
    fill: #2c3e50;
  }
}
</style>
