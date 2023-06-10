<template>
  <div class="app-main">
    <router-view :key="key" />
  </div>
</template>

<script>
export default {
  name: 'AppMainDisplay',
  computed: {
    key() {
      return this.$route.path
    }
  }
}
</script>
