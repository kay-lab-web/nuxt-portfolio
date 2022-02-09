<template>
  <div class="Main">
    <Header />
    <FirstView />

    <div class="Section Section--glay Section--about" id="about">
      <section class="Section__inner">
        <h2 class="Heading Heading--center">About</h2>
        <dl class="Timeline">
          <dt class="Timeline__date">2016/12～</dt>
          <dd class="Timeline__content">Web制作会社でコーダー/フロントエンドエンジニアとして、webサイトの制作・保守、webアプリケーション・webサービスの開発・テスト・保守といったwebに関連する業務を3年10ヵ月経験する中で、地元広島を中心とする企業様の受託案件や代理店案件を中心にビジネス課題の解決に寄与して参りました。</dd>
        </dl>
        <dl class="Timeline">
          <dt class="Timeline__date">2020/10</dt>
          <dd class="Timeline__content">地元広島にて高級料亭を運営している企業内のweb制作担当として、webサイトのデザイン～制作～運用を1年程経験して参りました。</dd>
        </dl>
        <p class="Paragraph">これまでwebサイトやサービスの制作と幅広く携わってきた中でも、webサイトにおける実装を得意としております。</p>
        <div class="Btn__wrap">
          <NuxtLink to="/archive/" class="Btn Btn--keyColor">実績一覧へ</NuxtLink>
        </div>
      </section>
    </div>

    <div class="Section Section--skills" id="skills">
      <h2 class="Heading Heading--center">Skills</h2>

      <h3 class="Heading Heading--small Heading--center">Design</h3>
      <div class="Bnr">
          <img src="~/assets/images/logo-xd.png" alt="">
          <img src="~/assets/images/logo-ps.png" alt="">
          <img src="~/assets/images/logo-ai.png" alt="">
      </div>

      <h3 class="Heading Heading--small Heading--center">Front-end</h3>
      <div class="Bnr">
        <img src="~/assets/images/logo-nuxt.png" alt="">
        <img src="~/assets/images/logo-sass.png" alt="">
        <img src="~/assets/images/logo-node-js.png" alt="">
        <img src="~/assets/images/logo-netlify.png" alt="">
      </div>

      <h3 class="Heading Heading--small Heading--center">CMS</h3>
      <div class="Bnr">
        <img src="~/assets/images/logo-wp.png" alt="">
        <img src="~/assets/images/logo-movabletype.png" alt="">
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'IndexPage'
}
</script>


<style lang="scss" scoped>
@import "~/assets/sass/_foundation/variables";
@import "~/assets/sass/_foundation/mediaqueries";

.Section {
  &--about {
    padding: 120px 0;
    @include mq-max(content) {
      padding: 120px $contentPadding 120px;
    }
    @include mq-max(xs) {
      padding: 50px $contentPadding 50px;
    }
  }
}

.Section__inner {
  max-width: $xs;
  margin: 0 auto;
}

.Timeline {
  position: relative;
  padding-left: 3rem;
  margin-bottom: 1rem;

  &::before {
    content: "";
    position: absolute;
    top: 1rem;
    left: 9px;
    width: 2px;
    height: calc(100% + 1rem);
    background-color: $mainColor;
  }
  &::after {
    content: "";
    position: absolute;
    left: 4px;
    top: 10px;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: $mainColor;
    z-index: 1;
  }
  &:last-of-type {
    margin-bottom: 4rem;
    &::before {
      background: linear-gradient(180deg, $mainColor 50%, $offWhite 75%);
    }
  }
  &__date {
    font-size: 1.33rem;
    &::before {
      content: "";
      position: absolute;
      left: 7px;
      top: 13px;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background-color: lighten($mainColor, 40%);
      animation: 1.2s ease-in-out infinite alternate forwards running Lamp;
      z-index: 2;
    }
  }
}


@keyframes Lamp {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.Paragraph {
  margin-bottom: 1rem;
}

.Bnr {
  display: flex;
  justify-content: center;
  margin-bottom: 50px;
  @include mq-max(sm) {
    flex-wrap: wrap;
  }
  @include mq-max(xs) {
    justify-content: flex-start;
    > img {
      width: 50%;
    }
  }
}
</style>