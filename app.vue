<template>
  <div></div>

  <div id="videoPlayerContainer" style="height: 400px; width: 500px">
    <video ref="videoPlayer" class="video-js video-player-box"></video>
  </div>
</template>
<script setup>
import videojs from "video.js";
import "video.js/dist/video-js.css";

// import "videojs-vr";
// ERROR return [nuxt] [request error] [unhandled] [500] Cannot use import statement outside a module

import "videojs-vr/dist/videojs-vr.js";
import "videojs-vr/dist/videojs-vr.css";
//ERROR: return navigator is not defined

const videoPlayer = ref(null);
let player = null;
onMounted(() => {
  player = videojs(videoPlayer.value, {
    playsinline: true,
    autoplay: false,
    controls: true,
    language: "en",
    fluid: true,
    preload: "none",
    sources: [
      {
        src: "/eagle-360.mp4",
        type: "video/mp4",
      },
    ],
  });

  player.vr({ projection: "360" });
});
</script>
