<template>
  <div class="Main">
    <Header />
    <FirstView />

    <div class="Section Section--glay Section--about" id="about">
      <section class="Section__inner">
        <h2 class="Heading Heading--center">About</h2>
        <p class="Paragraph">
          2016/12より、Web制作会社でwebフロントエンドエンジニアとして、地元広島を中心とする企業のwebサイトの制作・保守、webアプリケーションの開発・テスト・保守までを4年弱経験した後、<br>
          2020/10より、飲食Gr.店を運営する企業内のwebデザイナー担当としてwebサイトのUXUIデザイン・運用を1年程経験して参りました。</p>
        <p class="Paragraph">これまでwebサイト、プロダクト、サービスと幅広く携わってきた中でも、UXリサーチ、webサイトデザインを得意としております。</p>
        <div class="Btn__wrap">
          <NuxtLink to="/archive/" class="Btn Btn--keyColor">実績一覧へ</NuxtLink>
        </div>
      </section>
    </div>

    <div class="Section Section--skills" id="skills">
      <h2 class="Heading Heading--center">Skills</h2>

      <h3 class="Heading Heading--small Heading--center">Front-end</h3>
      <div class="Bnr">
          <img src="~/assets/images/logo-nuxt.png" alt="">
          <img src="~/assets/images/logo-sass.png" alt=""><br>
          <img src="~/assets/images/logo-xd.png" alt="">
          <img src="~/assets/images/logo-ps.png" alt="">
      </div>

      <h3 class="Heading Heading--small Heading--center">Tools</h3>
      <div class="Bnr">
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