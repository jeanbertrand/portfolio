<template>
  <section class="container-fluid">
    <Navigation/>
    <div class="body-container">
      <main class="container wrapper">
        <div class="headline">
          <h1>Contact Me</h1>
        </div>
        <form name="contact" netlify>
          <p>
            <label>Name <input type="text" name="name" /></label>
          </p>
          <p>
            <label>Email <input type="email" name="email" /></label>
          </p>
          <p>
            <button type="submit">Send</button>
          </p>
        </form>
      </main>
    </div>
  </section>
</template>

<script>
import Navigation from '~/components/nav.vue'

export default {
  components: {
    Navigation
  }
}
</script>

<style lang="scss">

</style>
