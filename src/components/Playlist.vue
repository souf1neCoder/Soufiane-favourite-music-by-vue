<template>
  <section>
    <div class="container">
      <h3>Playlist (Soufiane Mood) <i class="fas fa-heartbeat"></i></h3>
      <div class="buttons">
        <button
          v-for="song in songs"
          :key="song.src"
          @click="$emit('play_click', song)"
          :class="song.src == current.src ? 'song playing' : 'song'"
        >
          {{ song.artist }} - {{ song.title }}
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    songs: Array,
    current: Object,
  },
};
</script>

<style scoped>
h3 {
  text-align: center;
  margin-bottom: 15px;
  color: black;
}
button {
  margin: 0.5rem auto;
  color: var(--dark-color);
  appearance: none;
  background: #fff;
  padding: 10px;
  border-radius: 5px;
  font-size: 1.1rem;
  width: 80%;
  border: none;
  outline: none;
  transition: 0.3s ease;
  font-weight:500;
  cursor: pointer;
}
.fa-heartbeat {
  color: var(--primary-color);
}
.buttons {
  text-align: center;
  margin-bottom: 1.5rem;
}
button:hover {
  background: var(--primary-color);
  color: #fff;
}
button:active {
  transform: scale(0.98);
}
button.playing {
  background: var(--primary-color);
  color: #fff;
}
@media only screen and (max-width: 700px) {
  button{
      width:100%;
  }
}
</style>
