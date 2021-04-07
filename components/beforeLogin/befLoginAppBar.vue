<template>
  <v-app-bar
    app
    :height="appBarHeight"
    color="white"
  >
    <nuxt-link
      to="/"
      class="text-decoration-none"
    >
      <app-logo />
    </nuxt-link>

    <app-title
      class="hidden-mobile-and-down"
    />

    <v-spacer />

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
    appTitle,
    signupLink,
    loginLink
  },
  data ({ $store }) {
    return {
      appBarHeight: $store.state.styles.beforeLogin.appBarHeight
    }
  }
}
</script>
