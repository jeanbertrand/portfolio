<template>
  <div class="logo centered">
    <img src="img/jbu.png" />
  </div>
</template>

<style lang="scss">
@import '~assets/scss/main';

.logo {
  display: inline-block;
  animation: turn 2s linear forwards 1s;
  transform: rotateX(180deg);
  position: relative;
  overflow: hidden;
  max-width: 100px;
  margin: 2.75em;

  img {
    width: 100%
  }
}

@keyframes turn {
  100% {
    transform: rotateX(0deg);
  }
}

@keyframes godown {
  100% {
    top: 180px;
  }
}

@keyframes goright {
  100% {
    left: 70px;
  }
}
</style>
