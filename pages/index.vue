<template>
  <layout>
    <p class="color-white">
      Plenty of high-quality ports and some worthy original games on AppStore.
      Good luck finding them all, though
    </p>
    <p>
      Collecting "big" console ports, indie games that had steam release and some community recommendations all in a single page.
    </p>
    <main-grid :genres="genres" :games="games"> </main-grid>
  </layout>
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData({ $content }) {
    // getting document based on URL
    const allGames = await $content(`games/all-data`).fetch();
    const games = allGames.records;
    const genres = [];
    games
      .filter((g) => !!g)
      .forEach((game) => {
        if (game.genres) {
          game.genres.forEach((genre) => {
            if (!genres.includes(genre.slug)) {
              genres.push(genre.name);
            }
          });
        }
      });
    return { games, genres };
  },
};
</script>
<style>
</style>
