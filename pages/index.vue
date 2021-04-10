<template>
  <div class="container">
    <h1>Nuxt, Strapi, Postres, REST</h1>
    <div v-for="article in articles" :key="article.id">
      <div class="article">
        <NuxtLink :to="{ path: article.slug, query: { id: article.id } }">{{
          article.title
        }}</NuxtLink>
        <p>{{ article.subheading }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [],
    }
  },
  async mounted() {
    const response = await this.$axios.$get('articles')
    this.articles = response
  },
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  max-width: 800px;
}

h1 {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 50px;
  text-transform: uppercase;
  letter-spacing: 1px;
  text-align: center;
  margin: 30px 0;
}

.article {
  padding: 20px 0;
  border-bottom: 1px solid #d3d3d3;
  a {
    display: block;
    color: green;
    font-size: 30px;
    text-decoration: none;
    margin-bottom: 10px;
  }
}
</style>
