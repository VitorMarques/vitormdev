<template>
  <div class="container">
    <article>
      <nuxt-content :document="article" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    try {
      const article = await $content('articles/node', params.slug).fetch()
      return { article }
    } catch (err) {}
  },
}
</script>

<style scoped></style>
