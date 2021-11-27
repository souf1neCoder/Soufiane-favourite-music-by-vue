<template>
  <main>
    <div class="container">
      <div class="player">
        <h2 class="title_song">{{ current.artist }} - {{ current.title }}</h2>
        <div class="box_img">
          <img :src="current.img" alt="post" />
        </div>
        <div class="controls">
          <button @click="$emit('prev_click')" class="btn">
            <i class="fas fa-step-backward fa-2x"></i>
          </button>
          <button v-if="isPlaying" @click="$emit('pause_click')" class="btn">
            <i class="fas fa-pause fa-2x"></i>
          </button>
          <button v-if="!isPlaying" @click="$emit('play_click')" class="btn">
            <i class="fas fa-play fa-2x"></i>
          </button>
          <button @click="$emit('next_click')" class="btn">
            <i class="fas fa-step-forward fa-2x"></i>
          </button>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    current: Object,
    isPlaying: Boolean,
  },
};
</script>

<style scoped>
.player {
  text-align: center;
  margin: 100px auto;
}
.title_song {
  margin-bottom: 1rem;
  color: var(--dark-color);
  letter-spacing: 1px;
}
.box_img {
  width: 300px;
  height: 300px;
  margin: 0 auto 1.5rem auto;
}
.box_img img {
  max-width: 100%;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  border: 3px solid #fff;
  transition: 0.3s ease-in-out;
}
.box_img img:hover {
  box-shadow: 0 4px 10px #ccc;
}
button {
  border: none;
  background: #fff;
  width: 70px;
  appearance: none;
  height: 70px;
  margin: 0 5px;
  border-radius: 50%;
  color: var(--primary-color);
  cursor: pointer;
  transition: 0.3s ease-in-out;
}
@media only screen and (max-width: 700px) {
  .box_img {
    width: 250px;
    height: 250px;
  }
  .player {
    margin: 80px auto;
  }
}
</style>
