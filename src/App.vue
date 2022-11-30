<script setup lang="ts">
import sal from 'sal.js';
import Parallax from 'parallax-js';
import { onMounted, ref } from 'vue';
import SkillCard from './components/SkillCard.vue';

const backgroundIsloaded = ref(false);
const skills = ref([
  {
    title: 'JavaScript',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'TypeScript',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'Nest.js',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'Docker',
    img: 'https://png2.cleanpng.com/sh/484e4c6f2b97a99027bc94656de3a35f/L0KzQYm3VMA5N5dqfZH0aYP2gLBuTfRwa5xqip95eYTrf7A0kB9nfKhmitc2ZHXzfLFCjfVvfF59fdRyYXzkcsS0gB9vfJJuhtd7LUXkc7K5V8Nna2ZqTtcBLkS0R4e5UcA4OWY3S6MEN0e4SYm4UMYveJ9s/kisspng-docker-python-software-deployment-xebialabs-container-5aca273fc5e6e6.4176210715231977598106.png',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'K8s/Kubernetes',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'PostgreSQL',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'MongoDB',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'GraphQL',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'Vue.js',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'Nuxt.js',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'Rust',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'TDD',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
  {
    title: 'OOP',
    img: 'https://images.unsplash.com/photo-1479660656269-197ebb83b540?dpr=2&auto=compress,format&fit=crop&w=1199&h=798&q=80&cs=tinysrgb&crop=',
    desciption: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
  },
]);

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

  <!-- lottie files scroll -->
  <div id="second" class="w-full text-center flex flex-col items-center">
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
      class="w-9/12 mt-4"
      src="https://assets5.lottiefiles.com/packages/lf20_rK1iJW.json"
      >"
    </lottie-player>
  </div>

  <!-- skills card -->
  <div id="third" class="w-full text-center flex flex-col justify-center items-center">
    <h2
      class="text-gray-300 text-2xl md:text-4xl font-bold mb-16"
      data-sal-duration="2000"
      data-sal="slide-up"
      data-sal-repeat
      data-sal-delay="300"
      data-sal-easing="ease-out-back"
    >
      Skills
    </h2>

    <div class="flex flex-wrap justify-center py-10 px-20">
      <template v-for="skill in skills" :key="skill.title">
        <SkillCard :data-image="skill.img">
          <template v-slot:header
            ><h1>{{ skill.title }}</h1>
          </template>
          <template v-slot:content>
            <p>{{ skill.desciption }}</p>
          </template>
        </SkillCard>
      </template>
    </div>
  </div>

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
