<template>
<div id="app">
  <Navigation />
    <main>
         <p><nuxt-link to="/articles"> Back to posts </nuxt-link></p>
        <h1> {{article.title}} </h1>
        <p>Published on: {{new Date(article.publishedOn).toDateString() }}</p>
        <nuxt-content :document="article" />
        </main>
</div>
</template>

<script>
export default {
     async asyncData({ $content, route}) {
         const article = await $content(`articles/${route.params.slug}`).fetch();
         
         return {
             article
         }
    }
}
</script>
<style>
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-family: Helvetica, sans-serif;
}

a, a:visited {
  color: #215F5D
}

a:hover, a:visited:hover {
  color: #6DCCAB
}

h1 {
  font-size: 3rem;
}

.nuxt-content {
    margin: 1rem 4rem;
    text-align: left;
}

@media only screen and (max-width: 600px) {
.nuxt-content {
  margin: 1rem;
}
}
</style>