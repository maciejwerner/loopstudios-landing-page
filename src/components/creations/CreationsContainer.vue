<template>
  <div class="creations__container">
    <CreationsItem
      v-for="creation in creationsData"
      :key="creation.imageTitle"
      :creation="creation"
    />
  </div>
</template>

<script>
import creationsData from '@/utils/creationsData.js';
import CreationsItem from './CreationsItem.vue';

export default {
  name: 'CreationsContainer',
  components: {
    CreationsItem,
  },
  data() {
    return {
      creationsData: creationsData,
    };
  },
};
</script>

<style lang="scss" scoped>
.creations {
  &__container {
    display: grid;
    gap: 2rem;
    justify-items: center;
    align-items: center;
    grid-template-rows: auto;
  }

  @include media-tablet {
    .creations__container {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @include media-tablet-landscape {
    .creations__container {
      grid-template-columns: repeat(4, 1fr);
    }
  }
}
</style>
