<template>
  <section class="creations" id="creations">
    <div class="container">
      <div class="creations__header">
        <h2 class="title creations__title">Our creations</h2>
        <a href="#" class="creations__link" v-show="!mobile"> see all </a>
      </div>

      <CreationsContainer />

      <a
        href="#"
        class="creations__link creations__link--secondary"
        v-show="mobile"
      >
        see all
      </a>
    </div>
  </section>
</template>

<script>
import { ref, onMounted } from 'vue';
import CreationsContainer from './CreationsContainer.vue';

export default {
  name: 'Creations',
  components: {
    CreationsContainer,
  },
  setup() {
    let mobile = ref(null);
    let windowWidth = ref(null);

    onMounted(() => {
      checkScreen();
      window.addEventListener('resize', checkScreen);
    });

    const checkScreen = () => {
      windowWidth.value = window.innerWidth;

      if (windowWidth.value <= 768) {
        return (mobile.value = true);
      }

      mobile.value = false;
    };

    return {
      mobile,
      windowWidth,
      checkScreen,
    };
  },
};
</script>

<style lang="scss" scoped>
.creations {
  .container {
    padding: 3rem 0 5rem;
    display: grid;
    gap: 2rem;
  }

  &__title {
    font-size: var(--h2-font-size);
    text-align: center;
  }

  &__link {
    display: inline-block;
    padding: 0.35rem 2.35rem;

    background-color: $White;
    border: 1px solid $Black;
    color: $Black;
    font-family: $Font-Alata;
    font-size: var(--normal-font-size);
    font-weight: $Weight-300;
    letter-spacing: 4px;
    text-transform: uppercase;

    transition: color 300ms ease-in-out, background-color 300ms ease-in-out;

    &:focus,
    &:hover {
      color: $White;
      background-color: $Black;
    }

    &--secondary {
      margin: 0 auto;
    }
  }

  @include media-tablet {
    .creations__header {
      @include flex(row, center, space-between);
    }
  }
}
</style>
