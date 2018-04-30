<template>
  <section class="container-fluid">
    <NavBar/>
    <div class="container">
        <div class="page-header wrapper">
          <h2>Projects</h2>
        </div>
      <div class="card-columns">
        <div class="card portfolio-item item" v-for="post in posts" >
          <portfolio-item :post="post"></portfolio-item>
        </div>
      </div>
    </div>
  </section>

</template>

<script>
import NavBar from '~/components/Navbar.vue'
import {createClient} from '~/plugins/contentful.js'
import PortfolioItem from '~/components/portfolio-item.vue'

const client = createClient()

export default {
  asyncData ({ env, params }) {
    return client.getEntries({
      'content_type': env.CTF_BLOG_POST_TYPE_ID,
      order: '-fields.publishDate'
    }).then(entries => {
      return {
        posts: entries.items
      }
    })
  },
  components: {
    PortfolioItem,
    NavBar
  }
}
</script>

<style lang="scss">
@import '~assets/scss/main';

.page-header {

  h2 {
    color: $gray-light;
    text-align: center;
    padding: 2.5em 0;
  }
}

</style>
