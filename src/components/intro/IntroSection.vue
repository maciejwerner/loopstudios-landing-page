<template>
  <section class="about" id="about">
    <div class="container">
      <div class="about__item about__item--image"></div>
      <div class="about__item about__item--text">
        <h2 class="title about__title">The leader in interactive VR</h2>
        <p class="about__subtitle">
          Founded in 2011, Loopstudios has been producing world-class virtual
          reality projects for some of the best companies around the globe. Our
          award-winning creations have transformed businesses through digital
          experiences that bind to their brand
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Intro',
};
</script>

<style lang="scss" scoped>
.about {
  padding: 4rem 0;

  .container {
    @include flex(column, null, null);
    gap: 2rem;
  }

  &__item {
    &--image {
      position: relative;
      z-index: 5;
      background-image: url('~@/assets/images/mobile/image-interactive.jpg');
      background-position: center;
      background-repeat: no-repeat;
      background-size: cover;
      height: 22rem;
    }
  }

  &__title {
    font-size: var(--h2-font-size);
    margin-bottom: var(--mb-1);
    text-align: center;
  }

  &__subtitle {
    color: $Very-Dark-Gray;
    font-size: var(--normal-font-size);
    font-family: $Font-Alata;
    font-weight: $Weight-300;
    text-align: center;
  }

  @include media-tablet-landscape {
    padding: 6rem 0;

    .container {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(3, 1fr);
      gap: 2rem;
    }

    &__item {
      &--image {
        grid-column: 1 / 6;
        grid-row: 1 / -1;
        position: relative;
        z-index: 5;
        background-image: url('~@/assets/images/desktop/image-interactive.jpg');
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        height: auto;
      }

      &--text {
        grid-column: 5 / 13;
        grid-row: 2 / 4;
        position: relative;
        z-index: 10;
        align-self: flex-end;
        padding: var(--mb-5) 0 0 var(--mb-5);
        margin-left: -5rem;
        background: $White;
      }
    }

    &__title {
      text-align: left;
    }

    &__subtitle {
      text-align: left;
    }
  }
}
</style>
