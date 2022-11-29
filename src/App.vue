<script setup lang="ts">
// import { RouterLink, RouterView } from "vue-router";
import Parallax from 'parallax-js';
import { onMounted, ref } from 'vue';

const backgroundIsloaded = ref(false);

onMounted(() => {
  // preload image and set it to element style and listening to load event
  const imageUrl = '/cloud-bg.png';
  const bgElement: HTMLDivElement = document.querySelector('#scene')!;
  let preloaderImg = document.createElement('img');
  preloaderImg.src = imageUrl;
  preloaderImg.addEventListener('load', () => {
    bgElement.style.backgroundImage = `url(${imageUrl})`;
    backgroundIsloaded.value = true;

    // get scene element and pass to parallax lib
    const scene = document.getElementById('scene')!;
    new Parallax(scene, { hoverOnly: true });
  });
});
</script>

<template>
  <!-- biomousavi text with crystal parrallax -->
  <div id="scene" class="flex flex-col justify-center items-center min-h-screen">
    <div data-depth="0.2">
      <Transition name="fade">
        <h1 v-if="backgroundIsloaded">Biomousavi.</h1>
      </Transition>
    </div>
    <div data-depth="0.4">
      <Transition name="fade-bottom">
        <div v-if="backgroundIsloaded" class="scene-image"></div>
      </Transition>
    </div>
  </div>

  <div class="min-h-screen"></div>

  <!-- lottie files laptop scroll -->

  <!-- skills card animation -->

  <!-- lovely places with overdrive -->
</template>

<style>
#scene {
  overflow: hidden;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}
#scene div {
  width: 100%;
  height: 100%;
  text-align: center;
}
#scene div div {
  background-image: url('/people.png');
  position: absolute;
  width: 120%;
  left: -15%;
  backface-visibility: hidden;
  bottom: -6%;
  background-position: center top;
  background-size: cover;
  height: 230px;
}

#scene h1 {
  --bg-size: 400%;
  font-size: 10vw;
  margin-bottom: 15%;
  font-weight: bold;
  --color-one: #00000a;
  --color-two: #dddede;
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
@media (max-width: 640px) {
  #scene h1 {
    font-size: 15vw;
    margin-bottom: 70%;
  }
}
</style>
