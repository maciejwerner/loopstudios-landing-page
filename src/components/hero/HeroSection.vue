<template>
  <header class="header">
    <Navigation />

    <div class="container">
      <div class="header__description">
        <h1 class="header__title">
          Immersive <br />
          experiences <br />
          that deliver
        </h1>
      </div>
    </div>
  </header>
</template>

<script>
import Navigation from '@/components/nav/Navigation.vue';

export default {
  name: 'Hero',
  components: {
    Navigation,
  },
};
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  height: 35rem;

  background-image: url('~@/assets/images/mobile/image-hero.jpg');
  background-size: 100% 35rem;
  background-repeat: no-repeat;
  background-position: top;

  &__description {
    display: inline-block;

    margin: 10rem auto 0;
    padding: 1rem 2rem 1rem 1rem;

    border: 2px solid $White;
  }

  &__title {
    color: $White;
    font-family: $Font-Josefin-Sans;
    font-weight: $Weight-300;
    font-size: clamp(40px, 6.5vw, 85px);
    line-height: 1.2;
    text-transform: uppercase;
  }

  @include media-mobile {
    height: 40rem;
    background-size: 100% 40rem;
  }

  @include media-tablet {
    height: 50rem;

    background-image: url('~@/assets/images/desktop/image-hero.jpg');
    background-size: 100% 50rem;
  }
}
</style>
