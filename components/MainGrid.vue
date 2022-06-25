<template>
  <section>
    <section v-for="genre in genres" :key="genre">
      <nuxt-link :to="'/genre/' + genre">
        <h3>{{ genre }} games</h3>
      </nuxt-link>
      <slider :cards="find(genre)"></slider>
    </section>
  </section>
</template>
<script>
import { Component, Prop, Vue } from "nuxt-property-decorator";
import * as _ from "lodash";

@Component()
export default class MainGrid extends Vue {
  @Prop() games;
  @Prop() genres;

  get slides() {
    if (!this.games) {
      return [];
    } else {
      return _.shuffle(this.games).splice(0, 5);
    }
  }
  find(genre) {
    return (this.games || []).filter(
      (g) => g && g.genres && g.genres.find((g) => g.name === genre)
    );
  }
  openNewTab(slide) {
    window.open(slide.href);
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
.carousel {
  height: 60vh;
  width: 90vw;
  margin: auto;
  overflow: hidden;
}


</style>
<style lang="scss">
.carousel-caption {
  top: 25%;
  text-shadow: 3px 3px 8px #333;
}
</style>
