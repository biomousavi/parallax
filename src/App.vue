<script setup lang="ts">
// import { RouterLink, RouterView } from "vue-router";
import Parallax from 'parallax-js';
import { onMounted } from 'vue';

onMounted(() => {
  var scene = document.getElementById('scene')!;
  var parallaxInstance = new Parallax(scene, {
    hoverOnly: true,
  });
});
</script>

<template>
  <!-- biomousavi text with crystal parrallax -->
  <div id="scene" class="flex flex-col justify-center items-center min-h-screen">
    <h1 data-depth="0.1">Biomousavi.</h1>

    <!-- src="/people.png" -->
    <div data-depth="0.4">
      <div class="image"></div>
    </div>
  </div>

  <div class="min-h-screen"></div>

  <!-- lottie files laptop scroll -->

  <!-- skills card animation -->

  <!-- lovely places with overdrive -->
</template>

<style scoped>
:root {
  --bg-color: hsl(0, 0%, 17%);
}

#app {
  background-color: var(--bg-color);
  overflow: hidden;
}

#scene {
  overflow: hidden;
  background-image: url('/cloud-bg.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}

#scene div {
  width: 100%;
  height: 100%;
}
#scene div div {
  /* width: 300%;
  height: 100%;
  position: absolute;
  background-size: auto 101%;
  background-position: center bottom; */

  background-image: url('/people.png');
  /* background-color: yellowgreen; */
  position: absolute;
  width: 120%;
  left: -5%;
  /* transform: translate3d(0, 0, 0); */
  /* transform-style: preserve-3d; */
  backface-visibility: hidden;
  /* background-image: url(../../images/wave-paint.png); */
  bottom: -10%;
  background-position: center top;
  /* background-repeat: no-repeat; */
  background-size: cover;
  height: 230px;
}

#scene h1 {
  --bg-size: 400%;
  margin-bottom: 15%;
  font-weight: bold;
  --color-one: #00000a;
  --color-two: #dddede;
  font-size: 10vw;
  background: linear-gradient(90deg, var(--color-one), var(--color-two), var(--color-one)) 0 0 /
    var(--bg-size) 100%;
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
  -moz-background-clip: text;
}

@media (prefers-reduced-motion: no-preference) {
  #scene h1 {
    animation: move-bg 14s linear infinite;
  }

  @keyframes move-bg {
    to {
      background-position: var(--bg-size) 0;
    }
  }
}
</style>
