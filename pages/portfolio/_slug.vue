<template>
  <section class="container">
    <Navigation/>
    <div class="body-container">
      <main class="container wrapper">
        <a href="/portfolio" class="tiny ion-android-arrow-back">Back</a>
        <div class="headline">
          <h1>{{ post.fields.title }}</h1>
        </div>
        <div class="tags">
          <nuxt-link
            v-for="tag in post.fields.tags"
            :key="tag"
            :to="{ name: 'tags-tag', params: { tag: tag }}" class="tag">{{ tag }}</nuxt-link>
        </div>
        <div>
          <div class="description">
            <vue-markdown>{{post.fields.description}}</vue-markdown>
            <hr>
            <vue-markdown>{{post.fields.body}}</vue-markdown>
          </div>
          <div class="gallery" >
            <no-ssr><Flickity ref="Flickity" :options="flickityOptions" >
              <img v-for="image in post.fields.images" :key="image" :src="image.fields.file.url" class="carousel-image" :data-flickity-lazyload="image.fields.file.url">
            </Flickity></no-ssr>
          </div>
        </div>
      </main>
    </div>
  </section>
</template>

<script>
import VueMarkdown from 'vue-markdown'
import {createClient} from '~/plugins/contentful.js'
import Navigation from '~/components/nav.vue'

// plugins/vue-flickity.js

import Vue from 'vue';
import Flickity from 'vue-flickity';

Vue.component('Flickity', Flickity);

const client = createClient()

export default {
  asyncData ({ env, params }) {
    return client.getEntries({
      'content_type': env.CTF_BLOG_POST_TYPE_ID,
      'fields.slug': params.slug,
      'fields.images': params.images
    }).then(entries => {
      return {
        post: entries.items[0]
      }
    })
    return {
      flickityOptions: {
      initialIndex: 3,
      prevNextButtons: false,
      pageDots: false,
      wrapAround: true

      // any options from Flickity can be used
      }
    }
    .catch(console.error)
  },

  components: {
    Navigation,
    VueMarkdown
  }
}
</script>

<style lang="scss">
@import '~assets/scss/main';

* { box-sizing: border-box; }

.container.wrapper {
  padding-left:0;
  padding-right:0;
  max-width: 860px;
}

.gallery {
  padding-top:2em;
  p {
    img {
      margin:0 auto;
      padding: 2em 0;
      border-bottom: 1px solid $gray-lightest;
    }
  }

  .carousel {
    background: #EEE;

    .carousel-image {
      display: block;
      height: 300px;
      /* set min-width, allow images to set cell width */
      min-width: 150px;
      max-width: 100%;
      margin-right: 10px;
      /* vertically center */
      top: 50%;
      transform: translateY(-50%)
    }

    &.is-fullscreen {
      .carousel-image {
        height: auto;
        max-height: 100%;
      }
    }

  }

}
</style>
