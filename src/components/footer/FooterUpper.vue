<template>
  <div class="container">
    <div class="footer__column">
      <a
        href="#"
        class="footer__link"
        target="_blank"
        rel="nofollow noreferrer"
      >
        <LogoIcon />
      </a>

      <ul class="footer__menu" role="list">
        <li class="menu__item" v-for="link in navLinks" :key="link.path">
          <a :href="link.path" class="menu__link" :title="link.title"
            >{{ link.name }}
          </a>
        </li>
      </ul>
    </div>

    <div class="footer__column">
      <ul class="footer__socials">
        <li class="socials__item" v-for="link in socialLinks" :key="link.path">
          <a
            :href="link.path"
            class="socials__link"
            target="_blank"
            rel="nofollow noreferrer"
            :title="link.title"
          >
            <component :is="link.icon" />
          </a>
        </li>
      </ul>

      <p class="footer__copyright">
        &copy; 2022 Loopstudios. All rights reserved
      </p>
    </div>
  </div>
</template>

<script>
import NavLinks from '@/utils/navData.js';
import FacebookIcon from '@/layout/icons/FacebookIcon.vue';
import InstagramIcon from '@/layout/icons/InstagramIcon.vue';
import LogoIcon from '@/layout/icons/LogoIcon.vue';
import PinterestIcon from '@/layout/icons/PinterestIcon.vue';
import TwitterIcon from '@/layout/icons/TwitterIcon.vue';
import { markRaw } from 'vue';

export default {
  name: 'FooterUpper',
  components: {
    FacebookIcon,
    InstagramIcon,
    LogoIcon,
    PinterestIcon,
    TwitterIcon,
  },
  data() {
    return {
      navLinks: NavLinks,
      socialLinks: [
        {
          path: '#',
          icon: markRaw(FacebookIcon),
          title: 'Contact us on Facebook',
        },
        {
          path: '#',
          icon: markRaw(TwitterIcon),
          title: 'contact us on Twitter',
        },
        {
          path: '#',
          icon: markRaw(PinterestIcon),
          title: 'contact us on Pinterest',
        },
        {
          path: '#',
          icon: markRaw(InstagramIcon),
          title: 'contact us on Instagram',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 0 0 1.5rem;

  .footer__column {
    @include flex(column, null, null);
    gap: 1.35rem;
    text-align: center;
  }

  .footer__link {
    margin: 0 auto;
  }

  .footer__menu {
    padding: 1rem 0 2rem;

    .menu__item {
      display: block;
      padding-bottom: 1.125rem;
    }

    .menu__link {
      display: inline-block;
      position: relative;
      color: $White;
      font-family: $Font-Alata;
      font-weight: $Weight-300;
      font-size: var(--normal-font-size);
      text-transform: capitalize;

      @include hover-link-element($White, $White, -7px, 2px);
    }
  }

  .footer__socials {
    @include flex(row, center, center);
    gap: 1rem;

    .socials__link {
      display: inline-block;
      position: relative;

      @include hover-link-element($White, $White, -7px, 2px);
    }
  }

  .footer__copyright {
    color: $Dark-Gray;
    font-family: $Font-Alata;
    font-weight: $Weight-300;
    font-size: var(--normal-font-size);
  }

  @include media-tablet {
    @include flex(row, null, space-between);

    .footer__column {
      text-align: left;
      justify-content: center;
    }

    .footer__link {
      margin: 0;
    }

    .footer__menu {
      @include flex(row, center, null);
      gap: 1.5rem;
      padding: 0;
    }

    .footer__socials {
      @include flex(row, center, flex-end);
    }

    .footer__copyright {
      padding-bottom: 1.125rem;
    }
  }
}
</style>
