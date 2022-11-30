<script setup lang="ts">
import Parallax from 'parallax-js';
import sal from 'sal.js';

import { onMounted, ref } from 'vue';
const backgroundIsloaded = ref(false);

onMounted(() => {
  sal();

  // preload image and set it to element style and listening to load event
  const imageUrl = '/cloud-bg.webp';
  const bgElement: HTMLDivElement = document.querySelector('#scene')!;
  let preloaderImg = document.createElement('img');
  preloaderImg.src = imageUrl;
  preloaderImg.addEventListener('load', () => {
    bgElement.style.backgroundImage = `url(${imageUrl})`;
    backgroundIsloaded.value = true;

    // get scene element and pass to parallax lib
    const scene = document.getElementById('scene')!;
    new Parallax(scene, { hoverOnly: true });

    window.LottieInteractivity.create({
      mode: 'scroll',
      player: '#plant',
      container: '.cont',
      actions: [
        {
          visibility: [0, 1],
          type: 'seek',
          frames: [0, 450],
        },
      ],
    });
  });
});
</script>

<template>
  <!-- biomousavi text with crystal parrallax -->
  <div
    id="scene"
    class="flex flex-col justify-center bg-cover bg-no-repeat bg-center items-center min-h-screen overflow-hidden"
  >
    <div class="w-full h-full text-center" data-depth="0.05">
      <Transition name="fade">
        <h1 class="text-4xl md:text-8xl mb-16 font-bold" v-if="backgroundIsloaded">Biomousavi.</h1>
      </Transition>
    </div>

    <div class="w-full h-full" data-depth="0.4">
      <Transition name="fade-bottom">
        <div v-if="backgroundIsloaded" class="people absolute bg-cover"></div>
      </Transition>
    </div>
  </div>

  <div id="second" class="min-h-screen w-full text-center flex flex-col items-center">
    <h2
      class="text-gray-300 text-xl md:text-4xl mt-16 font-bold"
      data-sal-duration="2000"
      data-sal="slide-up"
      data-sal-repeat
      data-sal-delay="300"
      data-sal-easing="ease-out-back"
    >
      A Software Developer !
    </h2>

    <lottie-player
      id="plant"
      class="w-1/2 mt-10"
      src="https://assets5.lottiefiles.com/packages/lf20_rK1iJW.json"
      >"
    </lottie-player>
  </div>

  <div
    id="third"
    class="min-h-screen w-full text-center mt-32 flex flex-col justify-center items-center"
  ></div>

  <!-- lottie files laptop scroll -->

  <!-- skills card animation -->

  <!-- lovely places with overdrive -->
</template>

<style>
#scene .people {
  background-image: url('/people.webp');
  left: -12%;
  bottom: -6%;
  width: 120%;
  height: 230px;
  backface-visibility: hidden;
  background-position: center top;
}

#scene h1 {
  --bg-size: 400%;
  /* font-size: 10vw; */
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
  #scene div div {
    left: -20%;
    width: 180%;
    bottom: -12%;
  }
  #scene h1 {
    margin-bottom: 70%;
  }
}
</style>
