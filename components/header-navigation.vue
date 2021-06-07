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
}
</script>

<style lang="sass" scoped></style>
