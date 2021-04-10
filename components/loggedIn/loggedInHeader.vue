<template>
  <div>
    <logged-in-nav-drawer
      :drawer.sync="drawer"
    />
    <logged-in-app-bar>
      <template #nav-icon>
        <v-app-bar-nav-icon
          @click="drawer = !drawer"
        />
      </template>
    </logged-in-app-bar>
  </div>
</template>
<script>
import loggedInNavDrawer from '~/components/loggedIn/header/loggedInNavDrawer.vue'
import loggedInAppBar from '~/components/loggedIn/header/loggedInAppBar.vue'

export default {
  components: {
    loggedInNavDrawer,
    loggedInAppBar
  },
  data () {
    return {
      drawer: null
    }
  }
}
</script>
