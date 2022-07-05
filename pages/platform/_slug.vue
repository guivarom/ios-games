<template>
  <layout>
    <div class="container">
      <h1>Also available on {{ platformToFind }}  ({{ games.length }})</h1>
      <main-grid :games="games"/>
    </div>
  </layout>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    // getting document based on URL
    const allGames = await $content(`games/all-data`).fetch();
    const platformToFind = params.slug;
    const games = allGames.records
      .filter(
        (i) => i.platforms && i.platforms.map(p=>p.platform).find((plat) => plat.slug === platformToFind)
      )
      .filter((r) => !!r);
    return { games, platformToFind };
  },
};
</script>
<style scoped lang="scss">
</style>
