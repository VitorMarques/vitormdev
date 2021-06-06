<template>
  <div class="container-content">
    <div v-for="article in articles" :key="article.path" class="article">
      <div class="article-card">
        <div class="article-card__heading">
          <h1>
            <nuxt-link :to="article.path.replace('/articles', '')">{{
              article.title
            }}</nuxt-link>
          </h1>
          <p>Publicado em {{ formatDate(article.createdAt) }}</p>
        </div>
        <p class="article-card__description">{{ article.description }}</p>
      </div>
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

  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('pt-BR', options)
    },
  },
}
</script>

<style lang="sass" scoped>
@use "assets/sass/colors"

.container-content
  flex-direction: column

.article-card
  margin: 2rem 0
  &__heading
    h1
      margin-bottom: 0
    p
      margin: 0.1rem 0
      font-size: 14px
  &__description
    text-align: justify
    font-weight: 600
</style>
