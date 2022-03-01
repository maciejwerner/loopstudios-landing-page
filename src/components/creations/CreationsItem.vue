<template>
  <article class="creations__article">
    <a href="#" class="article__link">
      <figure class="article__figure">
        <picture>
          <source
            :srcset="require(`@/${creation.source.mobile}`)"
            media="(max-width: 991px)"
            data-media="mobile"
          />
          <source
            :srcset="require(`@/${creation.source.desktop}`)"
            media="(min-width: 992px)"
            data-media="desktop"
          />
          <img
            :src="require(`@/${creation.source.mobile}`)"
            :alt="creation.description.alt"
            data-media="mobile"
          />
        </picture>
        <figcaption class="article__figcaption">
          {{ creation.description.caption }}
        </figcaption>
      </figure>
    </a>
  </article>
</template>

<script>
export default {
  name: 'CreationsItem',
  props: {
    creation: {
      type: Object,
      default: () => ({
        source: {
          desktop: {
            type: String,
            default: '',
          },
          mobile: {
            type: String,
            default: '',
          },
        },
        description: {
          alt: {
            type: String,
            default: '',
          },
          caption: {
            type: String,
            default: '',
          },
          text: {
            type: String,
            default: '',
          },
        },
      }),
    },
  },
};
</script>

<style lang="scss" scoped>
.creations {
  &__article {
    .article__link {
      display: block;
      position: relative;
      z-index: 30;

      width: 100%;
      height: 100%;

      &::after {
        content: '';
        position: absolute;
        inset: 0;
        z-index: -1;

        background-color: linear-gradient(
          180deg,
          rgba(0, 0, 0, 0),
          rgba(0, 0, 0, 0.0001) 28.89%,
          rgba(0, 0, 0, 0.601863) 100%
        );

        transition: background-color 300ms ease-in-out;
        will-change: background-color;
      }

      &:focus,
      &:hover {
        &::after {
          background: rgba(250, 250, 250, 0.5);
          z-index: 1;
        }
      }

      &:focus .article__figcaption,
      &:hover .article__figcaption {
        color: $Black;
      }
    }

    .article__figcaption {
      width: 150px;

      position: absolute;
      bottom: 1rem;
      left: 1rem;
      z-index: 10;

      color: $White;
      font-size: clamp(1.35rem, 2vw, 1.75rem);
      font-family: $Font-Josefin-Sans;
      font-weight: $Weight-400;
      text-transform: uppercase;
      line-height: 1.1;

      transition: color 200ms ease-in-out;
      will-change: color;
    }
  }
}
</style>
