<template>
  <div>
    <header class="header container-full-width">
      <div class="container">
        <div class="header__logo">
          <h2>
            <nuxt-link to="/"> >_vitorm.dev </nuxt-link>
          </h2>
        </div>
        <header-navigation :key="activeTag" :tag="activeTag" />
      </div>
    </header>
    <div class="container-full-width">
      <Nuxt class="container" />
    </div>
    <footer class="footer container-full-width">
      <div class="container">
        <p>
          Desenvolvido com
          <a href="https://content.nuxtjs.org/" target="_blank">Nuxt</a> e com
          ❤️ por Vitor Marques
        </p>
        <ul>
          <li><nuxt-link to="/sobre-mim">sobre mim</nuxt-link></li>
          <li>
            <a href="https://github.com/VitorMarques" target="_blank">github</a>
          </li>
          <li>
            <a
              href="https://www.linkedin.com/in/vitor-marques-64a51410/"
              target="_blank"
              >linkedin</a
            >
          </li>
        </ul>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTag: '',
    }
  },
  watch: {
    $route() {
      this.activeTag = this.$route.path.split('/')[1]
    },
  },
}
</script>

<style lang="sass">
@use "assets/sass/colors"

.header
  border-top: 8px solid colors.$secondary-color
  height: 3.4rem
  margin-bottom: 1rem
  a
    color: colors.$secondary-color
  &__navigation > ul
    list-style: none
    display: flex
    flex-direction: row
    li
      margin: 1rem
      a
        color: colors.$secondary-color
        font-weight: bold

.footer
  margin: 1.2rem 0
  padding-top: 0.6rem
  .container
    display: flex
    justify-content: center
  ul
    list-style: none
    display: flex
    flex-direction: row
    justify-content: flex-end
    align-items: center
    li
      margin: 1rem
      a
        color: colors.$primary-color
        font-weight: bold
</style>
