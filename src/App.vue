<template>
  <div id="app">
    <Nav />
    <Player
      @play_click="play"
      @pause_click="pause"
      @next_click="next"
      @prev_click="prev"
      :isPlaying="isPlaying"
      :current="current"
    />
    <Playlist :current="current" @play_click="play" :songs="songs" />
    <Footer />
  </div>
</template>

<script>
import Nav from "./components/Nav.vue";
import Player from "./components/Player.vue";
import Playlist from "./components/Playlist.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Nav,
    Player,
    Playlist,
    Footer,
  },
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: "Bled",
          artist: "Moha K & DJ Kayz",
          src: require("./assets/DJ Kayz feat. Moha K - Bled (Clip Officiel).mp3"),
          img: require("@/assets/roro.jpg"),
        },
        {
          title: "If We Have Each Other",
          artist: "Alec Benjamin",
          src: require("@/assets/Alec Benjamin - If We Have Each Other [Official Music Video].mp3"),
          img: require("@/assets/alec.jpg"),
        },
        {
          title: "Por favor",
          artist: "CHAOS",
          src: require("@/assets/CHAOS - Por favor ( OFFICIAL VIDEO ).mp3"),
          img: require("@/assets/chaos.jpg"),
        },
        {
          title: "Léo",
          artist: "ElGrandeToto",
          src: require("@/assets/ElGrandeToto - Léo.mp3"),
          img: require("@/assets/toto.jpg"),
        },
        {
          title: "Allah’ından Bul",
          artist: "Ezhel",
          src: require("@/assets/Ezhel - Allah’ından Bul (Live) _ ROUNDS _ Vevo.mp3"),
          img: require("@/assets/ezhel.jpg"),
        },
        {
          title: "Alerte",
          artist: "Flenn",
          src: require("@/assets/Flenn - Alerte [Clip Officiel] Beat by IZM.mp3"),
          img: require("@/assets/flenn.jpg"),
        },
        {
          title: "Amoriste",
          artist: "Furelise",
          src: require("@/assets/Furelise - Amoriste ( EXCLUSIVE Lyric Video ).mp3"),
          img: require("@/assets/furi.jpg"),
        },
        {
          title: "HOPE",
          artist: "MADD",
          src: require("@/assets/MADD - HOPE (Prod by HKey x Neyl).mp3"),
          img: require("@/assets/madd.jpg"),
        },
        {
          title: "A7LAM",
          artist: "OUENZA",
          src: require("@/assets/OUENZA - A7LAM - LYRICS.mp3"),
          img: require("@/assets/ouenza.jpg"),
        },
        {
          title: "Babour",
          artist: "Tawsen",
          src: require("@/assets/Tawsen - Babour (Official Visualizer).mp3"),
          img: require("@/assets/tawsen.jpg"),
        },
      ],
      player: new Audio(),
    };
  },
  methods: {
    play(song) {
      if (typeof song != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener("ended", this.next);
      this.isPlaying = true;
      console.log(this.player.src);
    },
    pause() {
      this.player.pause();
      this.isPlaying = false;
    },
    next() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    //this.player.play()
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600;700&display=swap");
:root {
  --primary-color: #eb3b5a;
  --dark-color: #171717;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}
body {
  background: #eee;
}
.container {
  width: 80%;
  margin: auto;
}
.btn:focus {
  outline: none;
}
.btn:hover {
  box-shadow: 0 4px 10px #ccc;
}
.btn:active {
  transform: scale(0.98);
}
</style>
