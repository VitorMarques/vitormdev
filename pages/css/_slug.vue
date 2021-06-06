<template>
  <div class="container-content">
    <article>
      <h1>{{ article.title }}</h1>
      <nuxt-content :document="article" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    try {
      const article = await $content('articles/css', params.slug).fetch()
      return { article }
    } catch (err) {}
  },
}
</script>

<style scoped></style>
