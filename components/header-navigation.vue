<template>
  <div class="header__navigation">
    <ul>
      <li>
        <nuxt-link
          :class="tag === 'javascript' ? 'text-javascript' : ''"
          to="/javascript"
          >javascript</nuxt-link
        >
      </li>
      <li>
        <nuxt-link :class="tag === 'node' ? 'text-node' : ''" to="/node"
          >node</nuxt-link
        >
      </li>
      <li>
        <nuxt-link :class="tag === 'vuejs' ? 'text-vuejs' : ''" to="/vuejs"
          >vuejs</nuxt-link
        >
      </li>
      <li>
        <nuxt-link :class="tag === 'css' ? 'text-css' : ''" to="/css"
          >css</nuxt-link
        >
      </li>
      <li>
        <nuxt-link :class="tag === 'sass' ? 'text-sass' : ''" to="/sass"
          >sass</nuxt-link
        >
      </li>
      <div class="search">
        <input
          v-model="searchQuery"
          class="search-input"
          type="search"
          autocomplete="off"
          placeholder="pesquisar"
        />
        <transition name="page">
          <ul v-if="articles.length" class="search-result">
            <li v-for="article of articles" :key="article.path">
              <nuxt-link :to="article.path.replace('/articles', '')">
                <span>{{ article.title }}</span>
              </nuxt-link>
            </li>
          </ul>
        </transition>
      </div>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HeaderNavigation',
  props: {
    tag: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      searchQuery: '',
      articles: [],
    }
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery || searchQuery.length < 3) {
        this.articles = []
        return
      }
      this.articles = await this.$content('articles', { deep: true })
        .search(searchQuery)
        .limit(10)
        .fetch()
    },
  },
}
</script>

<style lang="sass" scoped>
@use 'assets/sass/colors'
.search
  display: flex
  align-self: center
  flex-direction: column
  &-input
    padding: .6rem
    height: 1.8rem
    border: 1px solid rgba(0, 0, 0, .2)
    border-radius: 4px
  &-result
    position: absolute
    padding: 0
    margin: 2rem 0
    list-style: none
    border: 1px solid rgba(0, 0, 0, .2)
    border-radius: 4px
    background-color: colors.$background-color
    z-index: 9999
    span:hover
      color: colors.$title-text-color
      text-decoration: underline
</style>
