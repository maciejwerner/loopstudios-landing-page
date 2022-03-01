<template>
  <Hero />
  <Intro />
  <Creations />
  <Footer />
</template>

<script>
import Creations from '@/components/creations/CreationsSection.vue';
import Footer from '@/components/footer/Footer.vue';
import Hero from '@/components/hero/HeroSection.vue';
import Intro from '@/components/intro/IntroSection.vue';

export default {
  name: 'App',
  components: {
    Creations,
    Footer,
    Hero,
    Intro,
  },
};
</script>

<style lang="scss">
#app {
  width: 100%;
  min-height: 100vh;

  background: $White;
  line-height: 1.5;

  overflow-x: hidden;
}

.container {
  width: 90%;
  max-width: 1100px;
  margin: 0 auto;
}

.title {
  color: $Black;
  font-family: $Font-Josefin-Sans;
  font-weight: $Weight-300;
  text-transform: uppercase;
  line-height: 1.1;
}
</style>
