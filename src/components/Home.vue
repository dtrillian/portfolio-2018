<template>
  <section class="hero is-fullheight">

    <div class="hero-body">
      <div class="container has-text-centered">
        <h3 class="title is-2" id="my-name">
          <a href="https://www.linkedin.com/in/malikba/">
            Malik <strong>Baba Aïssa</strong>
          </a>
        </h3>
        <h4 class="subtitle is-4">Portfolio</h4>
      </div>
    </div>

    <div class="hero-foot">
      <div class="container">
        <div class="tabs is-centered">
          <ul>
            <li class="small-image">
              <a href="https://bulma.io">
                <img src="../assets/img/made-with-bulma--semiblack.png" alt="bulma logo">
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div v-for="bubble in bubbles" :key="bubble.posX" id="moving-bubbles">
      <Bubble :size="bubble.size" :posX="bubble.posX" />
    </div>
  </section>


</template>

<script>
import anime from 'animejs';
import Bubble from './Bubble';

const bubbles = (() => {
  const maxSize = 100;
  const minSize = 20;
  const res = [];

  for (let i = 0; i < 100; i += 1) {
    const size = (Math.random() * (maxSize - minSize)) + minSize;
    const posX = Math.random() * 95;
    res.push({ size, posX });
  }

  return res;
})();

export default {
  name: 'Home',
  components: {
    Bubble,
  },
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      bubbles,
    };
  },
};

window.onload = () => {
  anime(
    // {
    //   targets: '#my-name',
    //   translateY: [50, 0],
    //   opacity: [0, 1],
    //   delay: 500,
    //   duration: 4000,
    //   direction: 'alternate',
    //   loop: false,
    // },
    {
      targets: '#moving-bubbles .bubble',
      translateY: -500,
      delay: 500,
      opacity: 1,
      direction: 'alternate',
      loop: true,
      duration: (el, i) => Math.random() * (i * 1000),
    });
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .small-image {
    width: 10%;
  }

  .hero.is-fullheight:before {
    content: '';
    display: block;
    width: calc(100% - 10px);
    height: calc(100% - 10px);
    position: absolute;
    border: 1px solid #e8dfdf;
    margin: 5px;
  }
</style>
