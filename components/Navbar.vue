<template>
  <nav class="navbar navbar-expand-lg">
  <div class="container-fluid">
    <nuxt-link no-prefetch class="navbar-brand" to="/">Recommended IOS Games</nuxt-link>
    <nuxt-link no-prefetch class="navbar-brand" to="/about">About</nuxt-link>
  </div>
</nav>
</template>
<script>
import { Component, Vue } from 'nuxt-property-decorator'
@Component
export default class Navbar extends Vue {
}
</script>
<style lang="scss" scoped>
.navbar {
  background: black;
  height: 10vh;
}
</style>
