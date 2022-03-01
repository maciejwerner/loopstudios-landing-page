<template>
  <div class="container">
    <p class="footer__author">
      Challenge by
      <a
        href="https://www.frontendmentor.io/"
        target="_blank"
        rel="nofollow noreferrer"
        class="footer__link"
        aria-label="Go to Frontendmentor www page"
      >
        Frontend Mentor.
      </a>
      Coded by &copy; 2021
      <a
        href="/"
        class="footer__link"
        target="_blank"
        rel="nofollow noreferrer"
        aria-label="Go to author Github repository"
      >
        Maciej Werner
      </a>
    </p>
  </div>
</template>

<script>
export default {
  name: 'FooterLower',
};
</script>

<style lang="scss" scoped>
.container {
  padding: 1rem 0;

  border-top: 1px solid $Dark-Gray;
  text-align: center;

  .footer__author {
    color: $White;
    font-family: $Font-Alata;
    font-size: var(--smaller-font-size);
    font-weight: $Weight-300;
    word-break: break-word;
  }

  .footer__link {
    display: inline-block;
    position: relative;

    padding-inline: 0.2rem;

    color: $White;
    font-family: $Font-Josefin-Sans;
    font-style: italic;
    font-weight: $Weight-400;

    transition: color 300ms ease-in-out;

    @include hover-link-element($White, $White, -2px, 1px);
  }
}
</style>
