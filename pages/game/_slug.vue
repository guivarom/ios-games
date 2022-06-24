<template>
  <layout>
    <nuxt-content :document="doc" />
  </layout>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    // getting document based on URL
    const doc = await $content(`games/${params.slug}`).fetch();
    return { doc };
  },
};
</script>