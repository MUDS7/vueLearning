
<template>
    <div class="app">
      <h1>你好啊</h1>
      <Person/>
      <person_setup/>
      <person_computed/>
      <person_watch/>
    </div>
</template>

<script lang="ts" setup>
  import Person from './components/person.vue';
  import person_setup from './components/person_setup.vue';
  import person_computed from './components/person_computed.vue';
  import person_watch from './components/person_watch.vue';
  
</script>

<style scoped>
  .app{
    background-color: #ddd;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
  }
</style>
