<template>
  <section>
     <b-table stacked="sm" class="color-white" striped :items="games" :fields="fields">
       <!-- A custom formatted column -->
      <template #cell(cover)="data">
        <img :src="data.item.cover" :alt="data.title" class="cover"/>
      </template>
       <template #cell(title)="data">
        <a :href="data.item.href"  target="_blank" > {{data.item.title}}</a>
      </template>
       <template #cell(genres)="data">
        <span>
          <nuxt-link v-for="g in (data.item.genres || []).sort((a,b) => a.name - b.name)" :key="g.name" :to="'/genre/' + g.slug">
            {{g.name}}
          </nuxt-link>
        </span>
      </template>
     </b-table>
  </section>
</template>
<script>
import { Component, Prop, Vue } from "nuxt-property-decorator";
import * as _ from "lodash";

@Component()
export default class MainGrid extends Vue {
  @Prop() games;
  get fields() {
    return [
      'cover',
      { key: 'title', sortable: true },
      { key: 'price', sortable: true },
      'genres'
    ]
  }

  get slides() {
    if (!this.games) {
      return [];
    } else {
      return _.shuffle(this.games).splice(0, 5);
    }
  }
  find(query) {
    return (this.games || []).filter(
      (g) => g && g.genres && g.genres.find((genre) => genre.slug === query)
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

.cover {
  height: 10vh;
  width: auto;
}
</style>
<style lang="scss">
.carousel-caption {
  top: 25%;
  text-shadow: 3px 3px 8px #333;
}
.color-white td, .color-white th{
  color: white!important;
}
</style>
