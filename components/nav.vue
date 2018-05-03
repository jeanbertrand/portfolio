<template>
  <div class="container">
    <nav class="navbar navbar-light bg-white sticky-top justify-content-between">
      <a href="/" class="navbar-brand"><img src="/img/jbu.png" /></a>
        <span class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarToggleExternalContent" aria-controls="navbarToggleExternalContent" aria-expanded="false" aria-label="Toggle navigation"><svg class="lnr lnr-menu"><use xlink:href="#lnr-menu"></use></svg></span>
      <NavLinks/>
    </nav>
    <div class="collapse" id="navbarToggleExternalContent">
        <navigationlinks/>
    </div>
  </div>
</template>

<script>
import NavLinks from '~/components/nav-links.vue'

export default {
  components: {
    NavLinks
  }
}
</script>

<style lang="scss">
@import '~assets/scss/main';

.navbar {
  height: 80px;
  border-bottom: 1px solid $gray-lightest;
  padding: .5rem 0rem !important;
  margin-right:-15px;
  margin-left: -15px;

  .navbar-brand {
    display: block;
    padding-left: 0;

    img {
      height: 100%;
      max-height: 40px;
      max-width: 40px;
    }
  }

  span[aria-expanded="true"] {
    background-color: $gray-lightest;
  }

  &.navbar-light .navbar-toggler {
    border-color: $gray-lightest;
  }

  .lnr {
    display: inline-block;
    fill: $brand-primary;
    width: 1em;
    height: 1em;
    vertical-align: -0.05em;
  }

  @include media-breakpoint-down(xs) {
    .justify-content-between {
      height: auto;
      //justify-content: center !important;
    }

    .links {
      display: none;
    }

  }

  @include media-breakpoint-up(sm) {
    .navbar-toggler {
      display: none;
    }

  }

}

.collapse {
  margin: 0em -30px;
  padding-right: 15px;
  padding-left: 15px;
  background-color: white;
  @include dropdown-shadow;

  @include media-breakpoint-up(sm) {
    &.show {
      display: none !important;
    }
  }
}

</style>
