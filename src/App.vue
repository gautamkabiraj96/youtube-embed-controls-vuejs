<template>
  <div id="app">
    <div>
      <div class="np-credits">www.nightprogrammer.com</div>
      <section>
        <youtube
          :video-id="videoId"
          :player-width="500"
          :player-height="300"
          @ready="ready"
          @playing="playing"
        ></youtube>
      </section>
      <div class="np-ib np-button" @click="play">Play</div>
      <div class="np-ib np-button" @click="pause">Pause</div>
      <div class="np-ib np-button" @click="stop">Stop</div>
    </div>
  </div>
</template>

<script>
import { getIdFromURL } from "vue-youtube-embed";
let videoId = getIdFromURL("https://www.youtube.com/watch?v=24C8r8JupYY");

export default {
  name: "App",
  data() {
    return {
      videoId,
    };
  },
  methods: {
    ready(event) {
      this.player = event.target;
    },
    playing(event) {
      console.log("playing");
    },
    change() {
      //this.videoId = "use another video id";
    },
    stop() {
      this.player.stopVideo();
    },
    pause() {
      this.player.pauseVideo();
      console.log("paused");
    },
    play() {
      this.player.playVideo();
      console.log("paused");
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 15px 10px;
}
.np-ib {
  display: inline-block;
}
.np-button {
  margin-top: 10px;
  background: #0051ff;
  color: #ffffff;
  width: 80px;
  margin-right: 10px;
  text-align: center;
  padding: 4px 8px;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s;
}
.np-button:hover {
  background: #4e86ff;
  transition: all 0.3s;
}
.np-credits {
  font-size: 12px;
  padding-bottom: 14px;
}
</style>
