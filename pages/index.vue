<template>
  <div class="container">
    <div v-for="article in articles" :key="article.path">
      <h1>{{ article.title }}</h1>
      <p>{{ article.description }}</p>
      <p>{{ article.createdAt }}</p>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    try {
      const articles = await $content({ deep: true })
        .only(['title', 'description', 'createdAt'])
        .sortBy('createdAt', 'desc')
        .limit(10)
        .fetch()
      return { articles }
    } catch (err) {}
  },
}
</script>

<style></style>
