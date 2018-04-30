<template>
  <div>
    <div class="card-img-top">
      <img class="thumbnail"
        :src="post.fields.heroImage.fields.file.url + '?fit=scale&w=350&h=196'"
        :srcset="`${post.fields.heroImage.fields.file.url}?w=350&h=196&fit=fill 350w, ${post.fields.heroImage.fields.file.url}?w=1000&h=562&fit=fill 1000w, ${post.fields.heroImage.fields.file.url}?w=2000&h=1125&fit=fill 2000w`"
        sizes="(min-width: 1024px) 400px, 100vw"
      >
    </div>
    <div class="card-body">
      <h5 class="card-title"><nuxt-link :to="{ name: 'blog-slug', params: { slug: post.fields.slug }}" class="title">{{ post.fields.title }}</nuxt-link></h5>

      <div class="tags">
        <nuxt-link
          v-for="tag in post.fields.tags"
          :key="tag"
          :to="{ name: 'tags-tag', params: { tag: tag }}" class="tag">{{ tag }}</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
@import '~assets/scss/main';

.card-columns {
  padding-top: 1.75em;

  .card {
    border: 1px solid $gray-lightest;
    color: $brand-primary;
    @include dropdown-shadow;

    &:hover {
      text-decoration: none;
      box-shadow: none;
    }

    .card-img-top {
      min-height:160px;
      content: "Something";

      img {
        max-width: 100%;
      }
    }

    .card-title a {
      color: $brand-primary ;

      &:hover {
        text-decoration: none;
        color: $gray-light;
      }
    }

    .tags {
      padding : 1em 0;
      margin-bottom: 1em;
    }

    .tag:link,
    .tag:visited {
      color: rgba($gray-light, .6);
      text-decoration: none;
      display: inline-block;
      padding: .33333rem .5rem;
      margin-right: .5em;
      font-size: 12px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: $btn-letter-spacing;

    }

    .tag:active,
    .tag:hover,
    .tag:focus {
      color: #606060;
      border-color: #606060;
    }
  }
}


</style>
