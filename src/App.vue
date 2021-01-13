<template>
  <div id="app">
    <List />
  </div>
</template>

<script>
import List from './components/list/List.vue'

export default {
  name: 'App',
  components: {
    List
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 18px;
  letter-spacing: 0.4px;
}
</style>
