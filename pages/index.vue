<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        {{ content.intro.text }}
      </h1>
      <h2 class="subtitle">
        {{ content.subtitle.text }}
      </h2>
      <div class="links">
        <a
          href="https://threejs.org/"
          target="_blank"
          class="button--green"
        >
          {{ content.link_1.text }}
        </a>
        <a
          href="https://greensock.com/"
          target="_blank"
          class="button--grey"
        >
          {{ content.link_2.text }}
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import { mapState } from 'vuex';
export default {
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  components: {
    Logo
  },
  computed: {
    content () {
      return this.$store.state.home.data
  },
  ...mapState('auth', ['loggedIn', 'user'])
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
