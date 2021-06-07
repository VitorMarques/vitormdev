<template>
  <div class="container-content">
    <div class="profile">
      <img
        class="profile-image"
        src="@/assets/img/profile-picture.JPG"
        alt="vitorm-perfil"
      />
      <div class="profile-description">
        <p>Blog pessoal de <a href="#">Vitor Marques</a></p>
        <p>Artigos variados sobre front-end e desenvolvimento web</p>
      </div>
    </div>
    <div v-for="article in articles" :key="article.path" class="article">
      <div class="article-card">
        <div class="article-card__heading">
          <h1>
            <nuxt-link :to="article.path.replace('/articles', '')">{{
              article.title
            }}</nuxt-link>
          </h1>
          <p>
            {{ formatDate(article.createdAt) }} em
            <span
              class="article-card__tag"
              :class="'tag-' + article.tag.toLowerCase()"
              ><nuxt-link :to="article.tag.toLowerCase()">{{
                article.tag
              }}</nuxt-link></span
            >
          </p>
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
        .only(['title', 'description', 'createdAt', 'tag'])
        .sortBy('createdAt', 'desc')
        .limit(15)
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

.profile
  display: flex
  justify-content: flex-start
  flex-direction: row
  align-items: center
  padding-bottom: 2rem

  &-image
    border-radius: 50%
    width: 80px
    height: 80px
  &-description
    margin-left: 1rem
    flex-direction: column
    display: flex
    a
      color: colors.$title-text-color
      font-weight: bold
    p
      margin: 0
      padding: 0

.article-card
  margin: 2rem 0
  &__heading
    h1
      margin-bottom: 0
    p
      margin: 0.1rem 0
      font-size: 14px
      color: colors.$text-color
  &__description
    text-align: justify
  &__tag
    border-radius: 4px
    padding: .2rem .6rem
    a
      color: white
</style>
