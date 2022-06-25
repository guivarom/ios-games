<template>
  <div class="card">
    <a :href="game.href" target="_blank">
      <img loading="lazy" :src="game.cover" class="card-img-top" alt="" />
    </a>
    <span class="badge badge-success">{{ game.price }}</span>
    <h4 class="name">{{ game.title }}</h4>
  </div>
</template>
<script>
import { Component, Prop, Vue } from "nuxt-property-decorator";
@Component
export default class Layout extends Vue {
  @Prop({ type: Object, required: true }) game;
}
</script>
<style lang="scss" scoped>
.card {
  flex: 0 0 24vw;
  max-height: 22vh;
  margin-right: 0.5em;
  overflow: hidden;
  position: relative;
  padding: 0;
  .badge {
    position: absolute;
    bottom: 0;
    right: 0;
  }
  .name {
    position: absolute;
    bottom: -11px;
    left: 0;
    width: 18vw;
    background: rgba(33,33,33, .6);
    padding: 5px;
  }
  & a {
    height: 100%;
    width: 100%;
    display: block;
    & img {
      height: 100%;
      width: 100%;
      object-fit: cover;
    }
  }
}
</style>
