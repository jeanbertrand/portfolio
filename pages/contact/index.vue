<template>
  <section>
    <Navigation/>
    <div class="container">
      <div class="row justify-content-md-center mt-5">
        <div class="col-md-6 header mt-5">
          <h1>Contact Me</h1>
          <p>Interested in UX/UI and product design opportunities for web and mobile applications.</p>
        </div>
      </div>
      <div class="row justify-content-md-center mt-5">
        <form class="col-md-6" name="contact" method="POST" action="/portfolio" netlify-honeypot="bot-field" data-netlify="true">
          <input type="hidden" name="form-name" value="contact" />
          <div class="form-group">
            <input type="text" class="form-control" name="name" placeholder="Your Name">
          </div>
          <div class="form-group">
            <input type="text" class="form-control" name="email" placeholder="Email">
          </div>
          <div class="form-group">
            <textarea type="textarea" rows="6" class="form-control" name="message" placeholder="Message"></textarea>
          </div>
          <div class="hidden"><label>Don’t fill this out: <input name="bot-field"></label></div>
          <button type="submit" class="col-md-6 btn btn-primary">Send Message<span class="ion-android-send"></span></button>
        </form>
      </div>
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
@import '~assets/scss/variables';
@import '~assets/scss/buttons';

.header {
    h1 {
      text-align: left;
    }
    p {
      color: $gray-light;
    }
}

main {
  .row {

  }
  .form-control {
    color: $gray;
    border: 2px solid $gray-lightest;
    background-color: rgba($gray-lightest, .25);
    padding: .75rem;

    &:focus {
      box-shadow: none;
      border-color: rgba($brand-primary, .25);
    }
  }
}

.centered {
  text-align: center;
}

.hidden {
  display: none;
}
</style>
