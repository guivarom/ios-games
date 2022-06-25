<template>
  <div class="slider">
   <game-card class="card" v-for="item in cards" :key="item.href" :game="item" />
  </div>
</template>
<script>
import { Component, Prop, Vue } from 'nuxt-property-decorator'
@Component
export default class Slider extends Vue {
  @Prop({ type: Array, default: [] }) cards; 
}
</script>
<style lang="scss" scoped>
.slider {
  height: 33vh;
  overflow-x: auto;
  display: flex;
}
.card:hover {
  transform: scale(1.2);
  z-index: 2;
}
</style>
