<template>
  <ul class="nav__menu" role="menu">
    <li
      class="nav__item"
      data-control="li"
      v-for="link in navLinks"
      :key="link.path"
    >
      <a :href="link.path" class="nav__link" :title="link.title">
        {{ link.name }}
      </a>
    </li>
  </ul>
</template>

<script>
import navLinks from '@/utils/navData.js';

export default {
  name: 'DesktopMenu',
  data() {
    return {
      navLinks: navLinks,
    };
  },
};
</script>

<style lang="scss" scoped>
.nav {
  &__menu {
    @include flex(row, center, null);
  }

  &__item {
    display: inline-block;
    margin-left: 2rem;
  }

  &__link {
    display: block;

    font-family: $Font-Alata;
    font-size: var(--normal-font-size);
    text-transform: capitalize;

    @include hover-link-element($White, $White, -4px, 2px);
  }
}
</style>
