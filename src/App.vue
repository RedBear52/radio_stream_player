<template>
  <div class="container">
    <StreamPlayer />
  </div>
</template>

<script>
import StreamPlayer from './components/StreamPlayer.vue'
export default {
  name: 'App',
  components: {
    StreamPlayer,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
