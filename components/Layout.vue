<template>
  <div class="layout">
      <navbar class="nav"/>
      <section class="content">
      <slot />
      </section>
  </div>
</template>
<script>
import { Component, Vue } from 'nuxt-property-decorator'
@Component
export default class Layout extends Vue {
}
</script>
<style lang="scss" scoped>
.layout {
    color: white;
    background: #111;
}
.content {
   padding: 2em;
}
.nav {
  position: sticky;
  top: 0;
  z-index: 1;
}
</style>
