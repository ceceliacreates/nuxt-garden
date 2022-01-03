<template>
    <main>
        <h1>Posts</h1>
        <p v-if="selectedTag" class="filter"> Filtered by: {{selectedTag}}  <button @click="selectedTag = ''">Clear</button></p>
        <p v-else class="filter"> Click any tag to filter.</p>
        <ul>
            <li v-for="post in displayedPosts" :key="post.slug + post.createdAt"> <h2>
                <nuxt-link :to="`/posts/${post.slug}`">{{post.title}}
                </nuxt-link>
                </h2>
            <p>Last updated: {{new Date(post.updatedOn).toDateString() }}</p>
            <p class="description"> {{post.description}}</p>
        <div class="tags"><button v-for="tag in post.tags" :key="post.slug + tag" @click="selectedTag = tag"> {{tag}}</button></div>
        </li>
        </ul>
    </main>
</template>

<script>
export default {
    async asyncData({ $content}) {
      const posts = await $content("posts")
      .sortBy("updatedOn", "desc").fetch();
      
      return {
          posts
      }
    },
    head: {
    title: "CeceliaCreates.com",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" }
    ]
  },
    data: () => ({
        selectedTag: ''
    }),
    computed: {
        displayedPosts() {
            if (this.selectedTag) {
                return this.posts.filter(post => post.tags.includes(this.selectedTag))
            } else {
                return this.posts
            }
        }
    }
    
}
</script>
<style scoped>
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

ul {
  list-style: none;
  margin: 1rem 4rem;
  padding: 0rem;
}

@media only screen and (max-width: 600px) {
ul {
  margin: 1rem;
}
}

button {
    background-color: #00d4ff;
    border: none;
    border-radius: 12px;
    padding: .25rem .5rem;
    margin: .25rem;
    cursor: pointer;
}

.filter {
    font-weight: bold;
}
</style>