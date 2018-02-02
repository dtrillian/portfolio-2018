<template>
  <section class="hero is-fullheight is-primary">

    <div class="hero-body">
      <div class="container has-text-centered">
        <h3 class="title is-2">
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
                <img src="../assets/img/made-with-bulma--semiwhite.png" alt="bulma logo">
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .small-image {
    width: 10%;
  }
</style>
