<template>
  <div class="app-wrapper">
    <div>
      <app-main-display />
    </div>
  </div>
</template>

<script>
import ResizeMixin from './../mixin/ResizeHandler'
import AppMainDisplay from "../components/AppMainDisplay";

export default {
  name: 'LayoutDisplay',
  components: {
    AppMainDisplay,
  },
  mixins: [ResizeMixin],
  computed: {
  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
  @import "~@/assets/styles/mixin.scss";
  @import "~@/assets/styles/variables.scss";

  .app-wrapper {
    height: 100px;
  }
</style>
