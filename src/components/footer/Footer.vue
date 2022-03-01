<template>
  <footer class="footer">
    <FooterUpper />
    <FooterLower />
  </footer>
</template>

<script>
import FooterLower from './FooterLower.vue';
import FooterUpper from './FooterUpper.vue';

export default {
  name: 'Footer',
  components: {
    FooterLower,
    FooterUpper,
  },
};
</script>

<style lang="scss" scoped>
.footer {
  width: 100%;

  padding: 2rem 0 0;
  background-color: $Black;
}
</style>
