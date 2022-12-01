<script setup lang="ts">
import sal from 'sal.js';
import Parallax from 'parallax-js';
import { onMounted, ref } from 'vue';
// const SkillCard = defineAsyncComponent(() => import('./components/SkillCard.vue'));

const backgroundIsloaded = ref(false);
// const skills = ref([
//   {
//     title: 'JavaScript',
//     img: 'https://images.pexels.com/photos/383640/pexels-photo-383640.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'JavaScript, often abbreviated as JS, is a programming language that is one of the core technologies of the World Wide Web, alongside HTML and CSS. ',
//   },
//   {
//     title: 'TypeScript',
//     img: 'https://images.pexels.com/photos/3894157/pexels-photo-3894157.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'TypeScript is a free and open source programming language developed and maintained by Microsoft. It is a strict syntactical superset of JavaScript and adds optional static typing to the language.',
//   },
//   {
//     title: 'Nest.js',
//     img: 'https://trilon.io/_nuxt/img/b471e1c.jpeg',
//     desciption:
//       'Nest. JS is a framework that helps build Node. JS server-side applications. The Nest framework is built using TypeScript which allows developers to build highly scalable and testable applications.',
//   },
//   {
//     title: 'Docker',
//     img: 'https://images.pexels.com/photos/3063470/pexels-photo-3063470.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. The service has both free and premium tiers.',
//   },
//   {
//     title: 'Kubernetes',
//     img: 'https://media.istockphoto.com/id/495907882/photo/common-octopus.jpg?b=1&s=612x612&w=0&k=20&c=2Mao1KQGywmK-Gk0AXfAX8i2Y30qoucTITd36TtVi9o=',
//     desciption:
//       'Kubernetes is an open-source container orchestration system for automating software deployment, scaling, and management.',
//   },
//   {
//     title: 'PostgreSQL',
//     img: 'https://images.pexels.com/photos/1750820/pexels-photo-1750820.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'PostgreSQL, also known as Postgres, is a free and open-source relational database management system emphasizing extensibility and SQL compliance.',
//   },
//   {
//     title: 'MongoDB',
//     img: 'https://images.pexels.com/photos/990349/pexels-photo-990349.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas.',
//   },
//   {
//     title: 'Vue.js',
//     img: 'https://images.pexels.com/photos/1407305/pexels-photo-1407305.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'Vue.js is an open-source model–view–viewmodel front end JavaScript framework for building user interfaces and single-page applications.',
//   },
//   {
//     title: 'Nuxt.js',
//     img: 'https://images.pexels.com/photos/1770809/pexels-photo-1770809.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'Nuxt.js is a free and open source JavaScript library based on Vue.js, Node.js, Webpack and Babel.js. Nuxt is inspired by Next.js, which is a framework of similar purpose, based on React.js.',
//   },
//   {
//     title: 'Rust',
//     img: 'https://images.pexels.com/photos/114108/pexels-photo-114108.jpeg?auto=compress&cs=tinysrgb&w=600',
//     desciption:
//       'Rust is a multi-paradigm, general-purpose programming language. Rust emphasizes performance, type safety, and concurrency.',
//   },
// ]);

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
  <div id="second" class="w-full text-center flex flex-col items-center mb-52">
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
  <!-- <div id="third" class="w-full text-center flex flex-col justify-center items-center">
    <div class="w-full flex justify-around items-center mb-16">
      <div
        data-sal-duration="2000"
        data-sal="slide-right"
        data-sal-repeat
        data-sal-delay="300"
        data-sal-easing="ease-out-back"
        style="height: 2px"
        class="w-1/3 bg-gray-300 rounded-full"
      ></div>
      <h2
        class="text-gray-300 text-2xl md:text-5xl font-bold"
        data-sal-duration="2000"
        data-sal="slide-up"
        data-sal-repeat
        data-sal-delay="300"
        data-sal-easing="ease-out-back"
      >
        Skills
      </h2>

      <div
        data-sal-duration="2000"
        data-sal="slide-left"
        data-sal-repeat
        data-sal-delay="300"
        data-sal-easing="ease-out-back"
        style="height: 2px"
        class="w-1/3 bg-gray-300 rounded-full"
      ></div>
    </div>

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
  </div> -->
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
  #scene .people {
    left: -20%;
    width: 180%;
    bottom: -16%;
  }
  #scene h1 {
    margin-bottom: 70%;
  }
}
</style>
