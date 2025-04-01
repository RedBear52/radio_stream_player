<template>
  <div class="stream-player">
    <img src="../assets/kdhx-logo.png" alt="kdhx-logo" width="100" />

    <h1>Listen Live</h1>
    <audio ref="audio" type=""></audio>
    <button :class="{ active: isPlaying }" @click="playStream">Play</button>
    <button :class="{ active: !isPlaying }" @click="stopStream">Stop</button>
  </div>
</template>

<script>
import { ref } from 'vue'

const streamUrl = 'https://proxy-stream-server.onrender.com/proxy-stream/live'
// const streamUrl = 'http://kdhx-ice.streamguys1.com/live'

export default {
  name: 'StreamPlayer',
  setup() {
    const audio = ref(null)
    const isPlaying = ref(false)

    const playStream = () => {
      if (audio.value) {
        audio.value.src = streamUrl
        audio.value.play()
        isPlaying.value = true
      }
    }

    const stopStream = () => {
      if (audio.value) {
        audio.value.pause()
        audio.value.src = ''
        isPlaying.value = false
      }
    }

    return {
      audio,
      isPlaying,
      playStream,
      stopStream,
    }
  },
}
</script>

<style lang="css" scoped>
.stream-player {
  text-align: center;
  margin: 20px;
}
h1 {
  font-size: 2em;
  margin-bottom: 20px;
}

button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 1em;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background-color: #e02024;
  color: white;

  transition: background-color 0.3s ease;
}

button:hover {
  background-color: black;
  color: white;
}

button.active {
  background-color: #ccc; /* Muted color for active button */
  color: white;
  cursor: not-allowed; /* Optional: indicate the button is inactive */
}
</style>
