<template>
  <div class="Section Section--firstview">
    <div class="Firstview">
      <div class="Firstview__inner">
        <h1 class="Firstview__title">Portfolio Site</h1>
        <p class="Firstview__scope">WebSite / Web Application / CMS <br> UXUI / WebDesign / Front-end </p>
        <div class="Firstview__decoration"></div>
        <div class="Firstview__copy">https://dreamy-mayer-b9da33.netlify.app/</div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "~/assets/sass/_foundation/variables";
@import "~/assets/sass/_foundation/mediaqueries";

.Section {
  &--firstview {
    position: relative;
    max-width: 100%;
    height: 100vh;
    @include mq-max(xs) {
      overflow: hidden;
    }
  }
}

.Firstview {
  max-width: $lg;
  margin: 0 auto;
  padding-top: 20rem;
  @include mq-max(se) {
    padding-top: 16.666rem;
  }
  &__title {
    color: $txtColor;
    font-size: 3rem;
    max-width: $sm;
    margin: 0 auto 0.5rem;
    transform: translateX(50px) translateY(-75px) rotate(-5deg);
    letter-spacing: .3rem;
    @include mq-max(sm) {
      transform: translateX(0) translateY(-75px) rotate(-5deg);
    }
    @include mq-max(xs) {
      font-size: 2.5rem;
    }
  }
  &__scope {
    max-width: $xs;
    margin: 0 auto;
  }

  &__decoration {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 0;
    height: 0;
    margin-top: -5rem;
    margin-left: -13.333rem;
    border-top: 420px $green solid;
    border-right: 242px transparent solid;
    border-left: 242px transparent solid;
    z-index: -1;
    transform: rotateZ(50deg);
    &:after {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 320px;
      height: 320px;
      margin-top: -330px;
      margin-left: -400px;
      box-sizing: border-box;
      border-radius: 50%;
      border: 1px $glay-l dashed;
      transform-origin: right top;
    }
  }
  &__copy {
    position: absolute;
    display: block;
    top: 25%;
    right: 18%;
    white-space: nowrap;
    font-size: 0.9rem;
    font-weight: 400;
    line-height: 0.9rem;
    letter-spacing: .4em;
    writing-mode: vertical-rl;
    @include mq-max(xs) {
      top: 22.5%;
      right: 9%;
    }
    &:after {
      content: '';
      position: absolute;
      top: 0;
      bottom: .2em;
      right: -1rem;
      width: 1px;
      background-color: $glay-l;
    }
  }
}

</style>