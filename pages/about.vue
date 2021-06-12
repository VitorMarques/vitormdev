<template>
  <div class="container-content">
    <nuxt-content :document="aboutMe" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    try {
      const aboutMe = await $content('about', 'about-me').fetch()
      return { aboutMe }
    } catch (err) {}
  },
}
</script>

<style scoped></style>
