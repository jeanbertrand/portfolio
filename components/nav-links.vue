<template>
  <div class="links">
    <a href="/portfolio" class="btn btn-link">Work</a>
    <a href="/resume" class="btn btn-link">Resume</a>
    <a href="/contact" class="btn btn-link">Contact</a>
  </div>
</template>

<style lang="scss">
@import '~assets/scss/main';

  .links {
    margin: 0;

    .btn {
      font-size: .85em;
      border: none;
    }

    @include media-breakpoint-down(xs) {

      .btn {
        width: 100%;
        padding: 1em .75em;
        border-bottom: 1px solid $gray-lightest;
      }
    }
  }

  .navbar .links {
    margin: 0;
  }
</style>
