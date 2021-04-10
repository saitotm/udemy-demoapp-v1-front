<template>
  <div />
</template>

<script>
export default {
  async middleware ({ store, redirect }) {
    await store.dispath('logout')
    return redirect('/')
  }
}
</script>
