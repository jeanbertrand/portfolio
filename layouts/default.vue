<template>
  <div class="container-fluid">
    <main role="main" class="theme_jbu">
      <nuxt/>
    </main>
  </div>
</template>

<script>
  
</script>

<style lang="scss">
@import '~assets/scss/main';

  body {
    background: rgba($gray-lightest, .5);
    margin: 1em auto;
    font-family: $font-family;
    font-size: 16px;
    line-height: 1.65;
    color: $gray;
  }

  .wrapper {
    padding: 2em 0;
    max-width: 80%;
    margin: 0 auto;
  }


  .page-bar {
    max-width: 100%;
    padding: 2em 10%;
  }

  .blog.header h2,
  .tag-page.header h2 {
    text-align: center;
    padding: 2.5em 0;
    color: #A0A0A0;
  }

  img {
    display: block;
    width: 100%;
  }

  h1,
  h2,
  h3 {
    font-size: 2em;
  }

  /* Copy section */
  .body-container {
    background: #ffffff;
  }


  *[class*="-bar"] {
    border-bottom: 1px solid $gray-lightest;
  }

</style>
