<template>
  <logged-in-container>
    <template #my-content>
      {{ $store.state.current.project }}
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
