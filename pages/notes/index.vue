<template>
<div id="app">
  <Navigation />
    <main>
        <h1>Notes</h1>
        <p v-show="selectedTag"> Filtered by: {{selectedTag}}  <button @click="selectedTag = ''">Clear</button></p>
        <ul>
            <li v-for="note in displayedNotes" :key="note.slug + note.createdAt"> <h2>
                <nuxt-link :to="`/notes/${note.slug}`">{{note.title}}
                </nuxt-link>
                </h2>
            <p>Published on: {{new Date(note.publishedOn).toDateString() }}</p>
            <p id="description"> {{note.description}}</p>
        <ul><li v-for="tag in note.tags" :key="note.slug + tag" @click="selectedTag = tag"> {{tag}}</li></ul>
        </li>
        </ul>
    </main>
</div>
</template>

<script>
export default {
    async asyncData({ $content}) {
      const notes = await $content("notes")
      .sortBy("publishedOn", "desc").fetch();
      
      return {
          notes
      }
    },
    data: () => ({
        selectedTag: ''
    }),
    computed: {
        displayedNotes() {
            if (this.selectedTag) {
                return this.notes.filter(note => note.tags.includes(this.selectedTag))
            } else {
                return this.notes
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

#description {
    font-style: italic;
}
</style>