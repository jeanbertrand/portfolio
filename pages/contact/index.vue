<template>
<section>
  <Navigation/>
    <header class="header">
      <div class="page-info wrapper">
          <h1>Contact Me</h1>
      </div>
    </header>
    <div class="container">
      <form class="offset-md-2 col-md-8" name="contact" method="POST" action="/portfolio" data-netlify="true">
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
        <div data-netlify-recaptcha></div>
        <button type="submit" class="col-md-4 btn btn-primary">Send Message<span class="ion-android-send"></span></button>
      </form>
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

header {
    h1 {
      text-align: center;
    }
}

main .form-control {
  color: $gray;
  border: 2px solid $gray-lightest;
  background-color: rgba($gray-lightest, .25);
  padding: .75rem;

  &:focus {
    box-shadow: none;
    border-color: rgba($brand-primary, .25);
  }
}

.centered {
  text-align: center;
}
</style>
