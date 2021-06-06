<template>
  <div>
    <header class="header container-full-width">
      <div class="container">
        <div class="header__logo">
          <nuxt-link to="/">
            <img src="@/assets/img/vitormdev-logo.png" alt="vitormdev-logo" />
          </nuxt-link>
        </div>
        <div class="header__navigation">
          <ul>
            <li><nuxt-link to="/javascript">javascript</nuxt-link></li>
            <li><nuxt-link to="/node">node</nuxt-link></li>
            <li><nuxt-link to="/vuejs">vuejs</nuxt-link></li>
            <li><nuxt-link to="/css">css</nuxt-link></li>
            <li><nuxt-link to="/sass">sass</nuxt-link></li>
          </ul>
        </div>
      </div>
    </header>
    <div class="container-full-width">
      <Nuxt
        :key="$route.fullPath"
        keep-alive
        :keep-alive-props="{ max: 20 }"
        class="container"
      />
    </div>
    <footer class="footer container-full-width">
      <div class="container">
        <p>Desenvolvido com Nuxt e com ❤️ por Vitor Marques</p>
      </div>
    </footer>
  </div>
</template>

<style lang="sass">
@use "assets/sass/colors"

.header
  background-color: colors.$secondary-color
  height: 3.4rem
  //border-top: 2px solid colors.$primary-color

  &__navigation > ul
    list-style: none
    display: flex
    flex-direction: row
    li
      margin: 1rem
      a
        color: colors.$background-color
        font-weight: bold

.footer
  display: flex
  flex-direction: column-reverse
  margin: 1.2rem 0
</style>
