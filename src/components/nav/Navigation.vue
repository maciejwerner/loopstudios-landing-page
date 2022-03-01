<template>
  <nav class="nav">
    <div class="container">
      <h2 class="nav__logo">
        <LogoIcon />
      </h2>

      <button
        type="button"
        class="nav__button"
        aria-controls="nav__menu"
        data-control="menu"
        v-show="mobile"
        @click="toggleHamburger"
      >
        <HamburgerIcon v-if="!mobileMenu" />
        <CloseIcon v-else />
      </button>

      <DesktopMenu v-show="!mobile" />
      <transition name="mobile-fade">
        <MobileMenu v-if="mobileMenu" />
      </transition>
    </div>
  </nav>
</template>

<script>
import { ref, onMounted } from 'vue';

import CloseIcon from '@/layout/icons/CloseIcon.vue';
import HamburgerIcon from '@/layout/icons/HamburgerIcon.vue';
import LogoIcon from '@/layout/icons/LogoIcon.vue';

import DesktopMenu from './DesktopMenu.vue';
import MobileMenu from './MobileMenu.vue';

export default {
  name: 'Navigation',
  components: {
    CloseIcon,
    HamburgerIcon,
    LogoIcon,
    DesktopMenu,
    MobileMenu,
  },
  setup() {
    let mobile = ref(null);
    let mobileMenu = ref(null);
    let windowWidth = ref(null);

    onMounted(() => {
      checkScreen();
      window.addEventListener('resize', checkScreen);
    });

    const toggleHamburger = () => {
      mobileMenu.value = !mobileMenu.value;
    };

    const checkScreen = () => {
      windowWidth.value = window.innerWidth;

      if (windowWidth.value <= 768) {
        return (mobile.value = true);
      }

      mobile.value = false;
      mobileMenu.value = false;
    };

    return {
      mobile,
      mobileMenu,
      windowWidth,
      toggleHamburger,
      checkScreen,
    };
  },
};
</script>

<style lang="scss" scoped>
/* mobile menu fade-in */
.mobile-fade-enter-active,
.mobile-fade-leave-active {
  transition: 300ms ease-in-out;
}

.mobile-fade-enter-from,
.mobile-fade-leave-to {
  transform: translateX(-100%);
}

.mobile-fade-enter-to {
  transform: translateX(0);
}

/* nav styles */
.nav {
  padding: 2rem 0;

  .container {
    @include flex(row, center, space-between);
  }

  &__logo {
    position: relative;
    z-index: 100;
  }

  &__button {
    position: relative;
    z-index: 100;
    display: inline-block;
    padding: 0.25rem;
  }
}
</style>

<style lang="scss">
.nav {
  &__menu {
    position: relative;
  }

  &__link {
    position: relative;

    color: $White;
    font-weight: $Weight-300;
  }
}
</style>
