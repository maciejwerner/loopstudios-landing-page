<template>
  <div class="menu__container" data-control="navMenu">
    <transition-group class="nav__menu" role="menu" tag="ul">
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
    </transition-group>
  </div>
</template>

<script>
import navLinks from '@/utils/navData.js';

export default {
  name: 'MobileMenu',
  data() {
    return {
      navLinks: navLinks,
    };
  },
};
</script>

<style lang="scss" scoped>
/* mobile menu fade-in */
// .mobile-list-fade-enter-active,
// .mobile-list-fade-leave-active {
//   transition: 300ms ease-in-out;
// }

// .mobile-list-fade-enter-from,
// .mobile-list-fade-leave-to {
//   transform: translateX(-100%);
//   opacity: 0;
// }

// .mobile-list-fade-enter-to {
//   transform: translateX(0);
// }

/* mobile items fade in */

.nav {
  .menu__container {
    height: 100%;

    position: fixed;
    inset: 0;
    z-index: 99;

    background: $Black;
  }

  &__menu {
    width: 90%;

    margin: 0 auto;
    padding: 10rem 0 0;

    @include flex(column, flex-start, null);
    row-gap: 2rem;
  }

  &__item {
    display: block;
  }

  &__link {
    display: inline-block;

    font-family: $Font-Josefin-Sans;
    font-size: var(--h3-font-size);
    font-weight: $Weight-400;
    text-transform: uppercase;

    @include hover-link-element($White, $White, -7px, 2px);
  }
}

@keyframes navLinkFade {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0px);
  }
}
</style>
