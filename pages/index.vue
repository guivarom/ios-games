<template>
 <layout>
<main-grid :genres="genres" :games="games"> </main-grid>
 </layout>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $content }) {
    // getting document based on URL
    const allGames = await $content(`games/all-data`).fetch();
    const games = allGames.records;
    const genres = [];
    console.log(allGames, games, genres, '!!!')
    games.filter(g => !!g).forEach (game => {
      if (game.genres) {
        game.genres.forEach(genre => {
          if (!genres.includes(genre.name)) {
            genres.push(genre.name)
          }
        })
      }
    })
    return { games, genres };
  }
}
</script>
