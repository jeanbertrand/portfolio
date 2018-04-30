<template>
  <section class="container">
    <NavBar/>
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
          </div>
          <div class="gallery">
            <vue-markdown>{{post.fields.body}}</vue-markdown>
          </div>
        </div>
      </main>
    </div>
  </section>
</template>

<script>
import VueMarkdown from 'vue-markdown'
import {createClient} from '~/plugins/contentful.js'
import NavBar from '~/components/Navbar.vue'

const client = createClient()

export default {
  asyncData ({ env, params }) {
    return client.getEntries({
      'content_type': env.CTF_BLOG_POST_TYPE_ID,
      'fields.slug': params.slug
    }).then(entries => {
      return {
        post: entries.items[0]
      }
    })
    .catch(console.error)
  },
  components: {
    NavBar,
    VueMarkdown
  }
}
</script>

<style lang="scss">
@import '~assets/scss/main';

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
}
.tags {
  margin: 1em 0 2em;
}

.tag:link,
.tag:visited {
  color: rgba($gray-light, .6);
  text-decoration: none;
  display: inline-block;
  padding: .33333rem .5rem;
  padding-left:0;
  margin-right: .5em;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: $btn-letter-spacing;

}

.tag:active,
.tag:hover,
.tag:focus {
  color: $brand-primary;
  border-color: transparent;
}

</style>
