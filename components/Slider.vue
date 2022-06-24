<template>
  <div class="slider">
    <div v-for="item in cards" :key="item" class="card">
      <img src="https://is3-ssl.mzstatic.com/image/thumb/Purple112/v4/76/87/7c/76877cec-b5ff-a8ae-dffa-f0710b23bc67/AppIcon-1x_U007emarketing-0-7-0-85-220.png/246x0w.webp" class="card-img-top" alt="" />
    </div>
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
.card {
  flex: 0 0 24vw;
  margin: 1em;
  max-height: 20vh;
  & img {
    height: 100%;
    object-fit: cover;
  }
}
</style>
