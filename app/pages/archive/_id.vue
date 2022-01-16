<template>
  <div class="Main" id="detail">
    <Header />
    <div class="Section">
      <h1 class="Heading Heading--center">{{items[$route.params.id - 1].title}}</h1>
      <div class="p-detail">
        <h2 class="p-detail__head">{{items[$route.params.id - 1].subtitle}}</h2>
        <div class="p-detail__info">
          <span class="p-detail__date">{{items[$route.params.id - 1].date}}</span>
          <div class="p-detail__cat">
            <span v-for="cat in items[$route.params.id - 1].category" :key="cat.category" :class="'Label Label--' + cat">{{cat}}</span>
          </div>
        </div>

        <div class="p-detail__inner">
          <div class="p-detail__contents">
            <h3 class="p-detail__head" v-if="items[$route.params.id - 1].feature01">特徴01</h3>
            <p class="p-detail__paragraph" v-html="items[$route.params.id - 1].feature01"></p>
            <h3 class="p-detail__head" v-if="items[$route.params.id - 1].feature02">特徴02</h3>
            <p class="p-detail__paragraph" v-html="items[$route.params.id - 1].feature02"></p>
            <h3 class="p-detail__head" v-if="items[$route.params.id - 1].results">成果</h3>
            <p class="p-detail__paragraph" v-html="items[$route.params.id - 1].results"></p>
            <div class="Btn__wrap">
              <router-link to="/archive/" class="Btn Btn--white">実績一覧へ</router-link>
              <a class="Btn" v-if="items[$route.params.id - 1].anchor" :href="items[$route.params.id - 1].anchor" target="_blank" rel="noopener">Webサイトはこちら</a>
            </div>
          </div>
          <div class="p-detail__images">
            <img :src="items[$route.params.id - 1].detailSrc">
            <!-- <img :src="items[$route.params.id - 1].detailSrc"> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="ts">
import ('../../assets/sass/pages/detail.scss');

import archives from '@/pages/archive/index.vue';
const datas = archives.data().items;

export default {
  name: 'detail',
  data() {
    return {
      name: "detail",
      items: datas
    }
  }
}
</script>