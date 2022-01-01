<template>
  <header class="Header">

    <div v-on:click="toggleMenu" class="Nav--Mobile" :class="{'Nav--active': isActive}">
      <span></span>
      <span></span>
      <span></span>
    </div>

    <nav class="Nav">
      <ul class="Nav__list">
        <li class="Nav__item"><NuxtLink to="/">Home</NuxtLink></li>
        <li class="Nav__item"><NuxtLink to="/">About</NuxtLink></li>
        <li class="Nav__item"><NuxtLink to="/">Skills</NuxtLink></li>
        <li class="Nav__item"><NuxtLink to="/">Archive</NuxtLink></li>
      </ul>
    </nav>

    <div class="FullscreenMenu" :class="[ isActive ? 'FullscreenMenu--open' : 'FullscreenMenu--close' ]">
      <div class="FullscreenMenu__bg"></div>
      <div class="FullscreenMenu__inner">
        <div class="FullscreenMenu__header">
          <div v-on:click="closeMenu" class="FullscreenCloseBtn">
            <span></span>
            <span></span>
            <span></span>
          </div>
        </div>
        <ul class="FullscreenMenu__nav">
          <li class="FullscreenMenu__item">
            <h2 class="FullscreenMenu__title">
              <NuxtLink to="/">Home</NuxtLink>
            </h2>
            <ul class="FullscreenMenu__rowNav">
              <li class="FullscreenMenu__item"><NuxtLink to="/" target="_blank" rel="noopener">About<font-awesome-icon icon="chevron-circle-right" style="font-size: 1em;" /></NuxtLink></li>
              <li class="FullscreenMenu__item"><NuxtLink to="/" target="_blank" rel="noopener">Skills<font-awesome-icon icon="chevron-circle-right" style="font-size: 1em;" /></NuxtLink></li>
              <li class="FullscreenMenu__item"><NuxtLink to="/" target="_blank" rel="noopener">Archive<font-awesome-icon icon="chevron-circle-right" style="font-size: 1em;" /></NuxtLink></li>
            </ul>
          </li>
        </ul>

      </div>
    </div>

  </header>
</template>

<script>
export default {
  data: () => {
    return {isActive: false}
  },
  methods: {
    toggleMenu () {
      this.isActive = !this.isActive
    },
    closeMenu () {
      this.isActive = !this.isActive
    },
    // SPメニューが開いた状態で、画面サイズが1024px以上の場合メニューをデフォルトの状態に戻す
    handleResize() {
      if (window.innerWidth <= 1024) {
          this.isActive = false
      }
    }
  },
  created() {
    window.addEventListener('resize', this.handleResize)
    this.handleResize()
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize)
  }
}
</script>
