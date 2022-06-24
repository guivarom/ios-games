<template>
  <layout>
    <section>
      <h3>Best games</h3>
      <slider :cards="cards1"></slider>
      <h3>Racing games</h3>
      <slider :cards="cards1"></slider>
      <h3>RPG games</h3>
      <slider :cards="cards1"></slider>
    </section>
  </layout>
</template>
<script>
import { Component, Vue } from "nuxt-property-decorator";
@Component
export default class MainGrid extends Vue {
  get cards1() {
    return [
      "Card 1",
      "Card 2",
      "Card 3",
      "Card 4",
      "Card 5",
      "Card 6",
      "Card 7",
      "Card 8",
    ];
  }
}
</script>
<style lang="scss" scoped>
.content {
  padding: 2em;
}
.nav {
  position: sticky;
  top: 0;
  z-index: 1;
}
.main-grid {
  height: auto;
}
</style>
