<template>
  <div>
    <section class="container">
      <div class="col-sm-12">
        <logo/>
        <h1>Jean-Bertrand Uwilingiyimana</h1>
        <NavLinks/>
        <ul class="social-icons">
            <li v-if='person.fields.twitter'>
              <a :href="person.fields.twitter" :aria-label="`${ person.fields.name } on Twitter`" target="_blank">
              <i class="icon ion-social-twitter"></use></i>
              </a>
            </li>
            <li v-if='person.fields.linkedIn'>
              <a :href="person.fields.linkedIn" :aria-label="`${ person.fields.name } on LinkedIn`" target="_blank">
                <i class="icon ion-social-linkedin"></use></i>
              </a>
            </li>
            <li v-if='person.fields.github'>
              <a :href="person.fields.github" :aria-label="`${ person.fields.name } on Github`" target="_blank">
                <i class="icon ion-social-github"></use></i>
              </a>
            </li>
          </ul>
      </div>
    </section>
  </div>
</template>

<script>
import {createClient} from '~/plugins/contentful.js'
import Logo from '~/components/nav-brand.vue'
import NavLinks from '~/components/nav-links.vue'

const client = createClient()

export default {
  asyncData ({env}) {
    return Promise.all([
      client.getEntries({
        'sys.id': env.CTF_PERSON_ID
      }),
      client.getEntries({
        'content_type': env.CTF_BLOG_POST_TYPE_ID,
        order: '-sys.createdAt'
      })
    ]).then(([entries, posts, projects]) => {
      return {
        person: entries.items[0],
        posts: posts.items
      }
    }).catch(console.error)
  },
  components: {
    Logo,
    NavLinks
  }
}
</script>

<style lang="scss">
@import '~assets/scss/main';

.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

</style>
