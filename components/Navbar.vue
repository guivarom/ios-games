<template>
  <nav class="navbar navbar-expand-lg">
  <div class="container-fluid">
    <a class="navbar-brand" href="/">IOS Games</a>
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
