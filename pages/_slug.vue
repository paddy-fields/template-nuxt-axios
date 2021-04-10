<template>
  <div class="container">
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <NuxtLink class="button" to="/">Back to home</NuxtLink>
  </div>
</template>

<script>
export default {
  data() {
    return {
      article: '',
    }
  },
  async mounted() {
    const response = await this.$axios.$get(`articles/${this.$route.query.id}`)
    this.article = response
  },
}
</script>

<style lang="scss">
.button {
  border: 2px solid green;
  color: green;
  text-decoration: none;
  padding: 10px 15px;
  font-size: 20px;
  display: inline-block;
  margin-top: 30px;
}
</style>
