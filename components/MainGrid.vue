<template>
  <section>
     <b-table-simple dark striped stacked="sm">
       <b-thead>
         <b-th></b-th>
         <b-th>Title</b-th>
         <b-th>Price</b-th>
         <b-th>Genres</b-th>
         <b-th>Screenshot</b-th>
         <b-th>Also available on</b-th>
       </b-thead>
      <b-tbody> 
        <b-tr v-for="item of games" :key="item.href">
          <b-td>
            <img :src="item.cover" loading="lazy" :alt="item.title" class="cover"/>
          </b-td>
          <b-td> <a :href="item.href">{{ item.title }}</a></b-td>
          <b-td stacked-heading="Price"> {{ item.price }} </b-td>
          <b-td stacked-heading="Genre">
            <a v-for="genre in item.genres"
              :key="genre.name"
              target="_blank"
              :href="'/ios-games/genre/' + genre.slug">
              {{ genre.name }}
            </a>
          </b-td>
          <b-td stacked-heading="Screenshot">
            <a v-if="item.screenshots && item.screenshots.length && item.screenshots.length > 1"
              target="_blank"
              class="with-delimiter"
              :href="item.screenshots[1].image">
              <img loading="lazy" style="max-height: 10vh;" :src="item.screenshots[1].image" />
            </a>
          </b-td>
          <b-td stacked-heading="Also on">
            <a v-for="p in (item.platforms || [])"
              class="with-delimiter"
              target="_blank"
              :key="p.platform.slug + '-' + item.href"
              :href="'/ios-games/platform/' + p.platform.slug">
            {{ p.platform.name }}
            </a>
          </b-td>
        </b-tr>
      </b-tbody>
     </b-table-simple>
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
      'title',
      'price',
      // { key: 'title' },
      // { key: 'price' },
      // 'genres',
      // { key: 'platforms', label: 'Also available on'}
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
  sortPlatforms(item) {
    return (item.platforms || []).sort((a,b) => a.platform.name - b.platform.name).filter(p => p.platform.name !== 'iOS')
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
.b-table-stacked-sm .cover {
  display: flex;
  margin: auto;
}
.with-delimiter::after {
  content: '|';
  color: white;
}
.with-delimiter:last-child:after {
  content: '';
  color: white;
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
