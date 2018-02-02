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

    <div id="moving-bubbles">
      <Bubble
        :size="bubble.size"
        :posX="bubble.posX"
        :randomColor="bubble.randomColor"
        v-for="bubble in bubbles"
        :key="bubble.posX"
      />
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
    let randomColor = `#${Math.floor(Math.random() * 16777215).toString(16)}`;
    res.push({ size, posX, randomColor });
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
    {
      targets: '#moving-bubbles .bubble',
      translateY: (el, i) => -Math.random() * i * 100,
      delay: 500,
      opacity: 0.7,
      direction: 'alternate',
      loop: true,
      duration: (el, i) => Math.random() * (i * 2000),
    },
  );

  anime(
    {
      targets: '#my-name',
      translateY: [50, 0],
      opacity: [0, 1],
      delay: 500,
      duration: 4000,
      direction: 'alternate',
      loop: false,
    },
  );
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .small-image {
    width: 10%;
  }

  .hero {
    z-index: 0;
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

  #moving-bubbles {
    display: block;
    position: absolute;
    z-index: 0;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }
</style>
