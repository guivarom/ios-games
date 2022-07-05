<template>
  <layout>
    <div class="container">
      <h1>{{ genreToFind }} games ({{ games.length }})</h1>
      <main-grid :games="games"/>
    </div>
  </layout>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    // getting document based on URL
    const allGames = await $content(`games/all-data`).fetch();
    const genreToFind = params.slug;
    const games = allGames.records
      .filter(
        (i) => i.genres && i.genres.find((genre) => genre.slug === genreToFind)
      )
      .filter((r) => !!r);
    return { games, genreToFind };
  },
};
</script>
<style scoped lang="scss">
</style>
