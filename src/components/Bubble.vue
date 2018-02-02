<template>
  <svg :width="size" :height="size" :viewBox="`0 0 ${size} ${size}`" class="bubble" xmlns="http://www.w3.org/2000/svg" :style="`left:${posX}%`">
    <defs>
      <linearGradient id="a" x1="50%" x2="50%" y1="100%" y2="0%">
        <stop offset="0%" stop-color="#D6D2FD"/>
        <stop offset="100%" stop-color="#FFF"/>
      </linearGradient>
    </defs>
    <circle
      :cx="`${size / 2}`"
      :cy="`${size / 2}`"
      :r="`${size / 2}`"
      fill="url(#a)"
      fill-rule="evenodd"
    />
  </svg>
</template>

<script>
// import anime from 'animejs';

export default {
  name: 'Bubble',
  props: ['size', 'posX'],
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
    };
  },
};

// window.onload = () => {
//   anime({
//     targets: '#moving-bubbles .bubble',
//     translateY: [-200, 2000],
//     delay: 500,
//     direction: 'alternate',
//     loop: true,
//     duration: (el, i) => 1000 + (i * 1000),
//   });
// };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .small-image {
    width: 10%;
  }

  .bubble {
    display: block;
    position: absolute;
    bottom: 0;
    opacity: 0;
    transform-origin: bottom center;
  }
</style>
