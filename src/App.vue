
<template>
    <div class="app">
      <h1>你好啊</h1>
      <Person/>
      <person_setup/>
    </div>
</template>

<script lang="ts">
  import Person from './components/person.vue';
  import person_setup from './components/person_setup.vue';
  export default {
    name:'App',
    components: { Person,person_setup },
  }
</script>

<style scoped>
  .app{
    background-color: #ddd;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
  }
</style>
