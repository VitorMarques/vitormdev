<template>
  <div>
    <header class="header">
      <div class="header-container">
        <div class="logo">
          <a href="/">
            <img src="@/assets/img/vitormdev-logo.png" alt="vitormdev-logo" />
          </a>
        </div>
        <div class="header-container__navigation">
          <ul>
            <li><a href="/javascript">javascript</a></li>
            <li><a href="/node">node</a></li>
            <li><a href="/vuejs">vuejs</a></li>
            <li><a href="/css">css</a></li>
            <li><a href="/sass">sass</a></li>
          </ul>
        </div>
      </div>
    </header>
    <Nuxt />
    <footer></footer>
  </div>
</template>

<style lang="sass">
@use "assets/sass/colors"

.header
  display: flex
  justify-content: center
  align-items: center
  background-color: colors.$secondary-color
  height: 3.4rem

  &-container
    width: 1140px
    display: flex
    justify-content: space-between
    align-items: center

    &__navigation > ul
      list-style: none
      display: flex
      flex-direction: row
      li
        margin: 1rem
        a
          color: colors.$background-color
          font-weight: 400
</style>
