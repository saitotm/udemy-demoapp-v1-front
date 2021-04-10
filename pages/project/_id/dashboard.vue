<template>
  <logged-in-container>
    <template #my-content>
      {{ $route.fullPath }}
    </template>
  </logged-in-container>
</template>

<script>
import loggedInContainer from '~/components/loggedIn/loggedInContainer.vue'

export default {
  components: {
    loggedInContainer
  }
}
</script>
