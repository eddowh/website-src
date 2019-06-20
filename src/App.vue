<template>
  <div id="app">
    <Website />
  </div>
</template>

<script>
import Website from './components/Website.vue';

export default {
  name: 'app',
  components: {
    Website,
  },
};
</script>

<style lang="scss">
#app {
  font-family: 'Franklin Gothic', 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
