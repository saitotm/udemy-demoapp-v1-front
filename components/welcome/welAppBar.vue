<template>
  <v-app-bar
    app
    :dark="!isScrollPoint"
    :height="appBarHeight"
    :color="toolbarStyle.color"
    :elevation="toolbarStyle.elevation"
  >
    <app-logo
      @click.native="goTo('scroll-top')"
    />

    <app-title
      class="hidden-mobile-and-down"
    />

    <!--
    <v-toolbar-title
      class="hidden-mobile-and-down"
    >
      {{ appName }}
    </v-toolbar-title>
    -->

    <v-spacer />

    <v-toolbar-items class="ml-2 hidden-ipad-and-down">
      <v-btn
        v-for="(menu, i) in menus"
        :key="`menu-btn-${i}`"
        text
        :class="{ 'hidden-sm-and-down': (menu.title === 'about') }"
        @click="goTo(menu.title)"
      >
        {{ $t(`menus.${menu.title}`) }}
      </v-btn>
    </v-toolbar-items>
    <signup-link />
    <login-link />
  </v-app-bar>
</template>

<script>
import loginLink from '../beforeLogin/loginLink.vue'
import signupLink from '../beforeLogin/signupLink.vue'
import appTitle from '../ui/appTitle.vue'
import appLogo from '~/components/ui/appLogo.vue'

export default {
  components: {
    appLogo,
    signupLink,
    loginLink,
    appTitle
  },
  props: {
    menus: {
      type: Array,
      default: () => []
    },
    imgHeight: {
      type: Number,
      default: 0
    }
  },
  data ({ $store }) {
    return {
      scrollY: 0,
      appBarHeight: $store.state.styles.beforeLogin.appBarHeight,
      isClient: process.client
    }
  },
  computed: {
    isScrollPoint () {
      return this.scrollY > (this.imgHeight - this.appBarHeight)
    },
    toolbarStyle () {
      const color = this.isScrollPoint ? 'white' : 'transparent'
      const elevation = this.isScrollPoint ? 4 : 0
      return { color, elevation }
    }
  },
  mounted () {
    if (this.isClient) {
      window.addEventListener('scroll', this.onScroll)
    }
  },
  beforeDestroy () {
    if (this.isClient) {
      window.removeEventListener('scroll', this.onScroll)
    }
  },
  methods: {
    onScroll () {
      this.scrollY = window.scrollY
    },
    goTo (id) {
      this.$vuetify.goTo(`#${id}`)
    }
  }
}
</script>
