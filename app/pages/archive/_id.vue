<template>
  <div class="Main">
    <Header />
    <div class="Contents">
      <div class="Section">
        <h1 class="Heading Heading--detail">
          <span v-if="items[$route.params.id - 1].id != 1 && items[$route.params.id - 1].id != 10" class="Heading__subtitle">{{items[$route.params.id - 1].anchor}}</span>
          {{items[$route.params.id - 1].title}}
        </h1>

        <!-- articleType == 1 -->
        <div v-if="items[$route.params.id - 1].articleType == 1" class="Detail Detail--col">
          <h2 class="Detail__head">{{items[$route.params.id - 1].subtitle}}</h2>
          <div class="Detail__info">
            <span class="Detail__date">{{items[$route.params.id - 1].date}}</span>
            <div class="Detail__cat">
              <span v-for="cat in items[$route.params.id - 1].category" :key="cat.category" :class="'Label Label--' + cat">{{cat}}</span>
            </div>
          </div>

          <div v-if="items[$route.params.id - 1].articleType == 1" class="Detail__article">
            <div class="Hero__images">
              <img :src="items[$route.params.id - 1].detailSrc" loading="lazy">
            </div>
            <div class="Overview">
              <h3 class="Overview__head" v-if="items[$route.params.id - 1].overview01">概要</h3>
              <div class="Overview__body">
                <p class="Overview__text" v-html="items[$route.params.id - 1].overview01"></p>
                <p class="Overview__text" v-html="items[$route.params.id - 1].overview02"></p>
              </div>
            </div>

            <div class="Detail__contents" v-if="items[$route.params.id - 1].title01">
              <div class="Detail__inner">
                <h3 class="Detail__head" v-html="items[$route.params.id - 1].title01"></h3>
                <p class="Detail__paragraph" v-html="items[$route.params.id - 1].description01"></p>
              </div>
            </div>

            <div class="Detail__contents">
              <div class="Detail__inner" v-if="items[$route.params.id - 1].title02 || items[$route.params.id - 1].description02">
                <h3 class="Detail__head" v-if="items[$route.params.id - 1].title02" v-html="items[$route.params.id - 1].title02"></h3>
                <p class="Detail__paragraph" v-if="items[$route.params.id - 1].description02" v-html="items[$route.params.id - 1].description02"></p>
              </div>

              <div class="Detail__image Detail__image--left" v-if="items[$route.params.id - 1].image01">
                <img :src="items[$route.params.id - 1].image01" loading="lazy">
              </div>
              <div class="Detail__image Detail__image--right" v-if="items[$route.params.id - 1].image02">
                <img :src="items[$route.params.id - 1].image02" loading="lazy">
              </div>
              <div class="Detail__image Detail__image--left" v-if="items[$route.params.id - 1].image03">
                <img :src="items[$route.params.id - 1].image03" loading="lazy">
              </div>

              <div class="Detail__inner" v-if="items[$route.params.id - 1].title03 || items[$route.params.id - 1].description03 ">
                <h3 class="Detail__head" v-html="items[$route.params.id - 1].title03"></h3>
                <p class="Detail__paragraph" v-html="items[$route.params.id - 1].description03"></p>
              </div>

              <div class="Detail__inner" v-if="items[$route.params.id - 1].title04">
                <h3 class="Detail__head" v-html="items[$route.params.id - 1].title04"></h3>
                <p class="Detail__paragraph" v-html="items[$route.params.id - 1].description04"></p>
              </div>

              <div class="Detail__inner" v-if="items[$route.params.id - 1].results">
                <h3 class="Detail__head" v-if="items[$route.params.id - 1].results">成果</h3>
                <p class="Detail__paragraph" v-html="items[$route.params.id - 1].results"></p>
              </div>

              <div class="Btn__wrap">
                <router-link to="/archive/" class="Btn Btn--white">実績一覧へ</router-link>
                <a class="Btn" v-if="items[$route.params.id - 1].anchor" :href="items[$route.params.id - 1].anchor" target="_blank" rel="noopener">{{items[$route.params.id -1 ].btnText}}</a>
                <a class="Btn" v-if="items[$route.params.id - 1].prototype" :href="items[$route.params.id - 1].prototype" target="_blank" rel="noopener">プロトタイプはこちら</a>
              </div>
            </div>
          </div>

        </div>
        <!-- articleType == 1 -->

        <!-- articleType == 2 -->
        <div v-if="items[$route.params.id - 1].articleType != 1" class="Detail Detail--row">
          <h2 class="Detail__head">{{items[$route.params.id - 1].subtitle}}</h2>
          <div class="Detail__info">
            <span class="Detail__date">{{items[$route.params.id - 1].date}}</span>
            <div class="Detail__cat">
              <span v-for="cat in items[$route.params.id - 1].category" :key="cat.category" :class="'Label Label--' + cat">{{cat}}</span>
            </div>
          </div>

          <div v-if="items[$route.params.id - 1].articleType != 1" class="Detail__inner Detail__inner--row">
            <div class="Detail__contents">
              <h3 class="Detail__head" v-if="items[$route.params.id - 1].feature01">概要</h3>
              <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature01"></p>
              <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature02"></p>
              <h3 class="Detail__head" v-if="items[$route.params.id - 1].results">成果</h3>
              <p class="Detail__paragraph" v-html="items[$route.params.id - 1].results"></p>
              <div class="Btn__wrap">
                <router-link to="/archive/" class="Btn Btn--white">実績一覧へ</router-link>
                <a class="Btn" v-if="items[$route.params.id - 1].anchor" :href="items[$route.params.id - 1].anchor" target="_blank" rel="noopener">{{items[$route.params.id -1 ].btnText}}</a>
              </div>
            </div>
            <div class="Detail__images">
              <img :src="items[$route.params.id - 1].detailSrc">
              <!-- <img :src="items[$route.params.id - 1].detailSrc"> -->
            </div>
          </div>

        </div>
        <!-- articleType == 2 -->
      </div>
    </div>
  </div>
</template>

<script>
import ('../../assets/sass/pages/detail.scss');

import archives from '@/pages/archive/index.vue';
const datas = archives.data().items;

export default {
  name: 'Detail',
  data() {
    return {
      items: datas
    }
  }
}
</script>