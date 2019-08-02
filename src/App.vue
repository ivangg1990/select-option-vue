<template>
  <div id="app">
    <SelectList />
  </div>
</template>

<script>
import SelectList from './components/SelectList.vue'

export default {
  name: 'app',
  components: {
    SelectList
  }
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
}
</style>
