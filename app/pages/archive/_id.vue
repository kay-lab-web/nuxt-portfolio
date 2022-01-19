<template>
  <div class="Main">
    <Header />

    <div class="Section" id="archives">
      <h1 class="Heading Heading--center">{{items[$route.params.id - 1].title}}</h1>

      <!-- articleType == 1 -->
      <div v-if="items[$route.params.id - 1].articleType == 1" class="Detail Detail--col">
        <h2 class="Detail__head">{{items[$route.params.id - 1].subtitle}}</h2>
        <div class="Detail__info">
          <span class="Detail__date">{{items[$route.params.id - 1].date}}</span>
          <div class="Detail__cat">
            <span v-for="cat in items[$route.params.id - 1].category" :key="cat.category" :class="'Label Label--' + cat">{{cat}}</span>
          </div>
        </div>

        <div v-if="items[$route.params.id - 1].articleType == 1" class="Detail__inner Detail__inner--row">
          <div class="Detail__images">
            <img :src="items[$route.params.id - 1].detailSrc" loading="lazy">
          </div>
          <div class="Detail__contents">
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].feature01">特徴01</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature01"></p>
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].feature02">特徴02</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature02"></p>
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].results">成果</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].results"></p>
            <div class="Btn__wrap">
              <router-link to="/archive/" class="Btn Btn--white">実績一覧へ</router-link>
              <a class="Btn" v-if="items[$route.params.id - 1].anchor" :href="items[$route.params.id - 1].anchor" target="_blank" rel="noopener">Webサイトはこちら</a>
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
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].feature01">特徴01</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature01"></p>
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].feature02">特徴02</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].feature02"></p>
            <h3 class="Detail__head" v-if="items[$route.params.id - 1].results">成果</h3>
            <p class="Detail__paragraph" v-html="items[$route.params.id - 1].results"></p>
            <div class="Btn__wrap">
              <router-link to="/archive/" class="Btn Btn--white">実績一覧へ</router-link>
              <a class="Btn" v-if="items[$route.params.id - 1].anchor" :href="items[$route.params.id - 1].anchor" target="_blank" rel="noopener">Webサイトはこちら</a>
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