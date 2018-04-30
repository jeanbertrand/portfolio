<template>
  <section class="container-fluid">
    <header class="article header">
        <NavBar/>
      <div>
        <!--<img
          :src="post.fields.heroImage.fields.file.url + '?fit=scale&w=350&h=196'"
          :srcset="`${post.fields.heroImage.fields.file.url}?w=350&h=87&fit=fill 350w, ${post.fields.heroImage.fields.file.url}?w=1000&h=250&fit=fill 1000w, ${post.fields.heroImage.fields.file.url}?w=2000&h=500&fit=fill 2000w`"
          size="100vw"
          :alt="post.fields.heroImage.fields.description"
        >-->
      </div>
    </header>

    <div class="body-container container">
      <main class="wrapper">
        <div class="headline">
          <h1>{{ project.fields.title }}</h1>
        </div>
        <div class="copy">
          <vue-markdown>{{project.fields.description}}</vue-markdown>
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
      'content_type': env.CTF_PROJECT_TYPE_ID,
      'field.slug': params.slug
    }).then(entries => {
      return {
        project: entries.items[0]
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

<style>

.foreground .page-bar {
  border-bottom: 0;
}

.headline {
  padding: 3em 0 0;
}

.headline h1 {
  font-size: 3.5em;
}

.copy {
  padding-bottom: 7em;
}

.copy *:not(div) {
  margin: 2em 0 1em;
}

.copy h3 {
  font-size: 1.35em;
}

.copy ul {
  margin: 0;
  padding-left: 1em;
  list-style: disc;
}

.copy li {
  margin: 0;
}

</style>
