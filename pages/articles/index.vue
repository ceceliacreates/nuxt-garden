<template>
<div id="app">
  <Navigation />
    <main>
        <h1> Articles</h1>
        <p v-show="selectedTag"> Filtered by: {{selectedTag}}  <button @click="selectedTag = ''">Clear</button></p>
        <ul>
            <li v-for="article in displayedArticles" :key="article.slug + article.createdAt"> <h2>
                <nuxt-link :to="`/articles/${article.slug}`">{{article.title}}
                </nuxt-link>
                </h2>
            <p>Published on: {{new Date(article.publishedOn).toDateString() }}</p>
            <p> {{article.description}}</p>
        <ul><li v-for="tag in article.tags" :key="article.slug + tag" @click="selectedTag = tag"> {{tag}}</li></ul>
        </li>
        </ul>
    </main>
</div>
</template>

<script>
export default {
    async asyncData({ $content}) {
      const articles = await $content("articles")
      .sortBy("publishedOn", "desc").fetch();
      
      return {
          articles
      }
    },
    data: () => ({
        selectedTag: ''
    }),
    computed: {
        displayedArticles() {
            if (this.selectedTag) {
                return this.articles.filter(article => article.tags.includes(this.selectedTag))
            } else {
                return this.articles
            }
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

ul {
  list-style: none;
  margin: 0rem;
  padding: 0rem;
}
</style>