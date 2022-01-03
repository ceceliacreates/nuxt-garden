<template>
    <main>
        <h1>Notes</h1>
        <p v-if="selectedTag" class="filter"> Filtered by: {{selectedTag}}  <button @click="selectedTag = ''">Clear</button></p>
        <p v-else class="filter"> Click any tag to filter.</p>
        <ul>
            <li v-for="note in displayedNotes" :key="note.slug + note.createdAt"> <h2>
                <nuxt-link :to="`/notes/${note.slug}`">{{note.title}}
                </nuxt-link>
                </h2>
            <p>Last updated: {{new Date(note.updatedOn).toDateString() }}</p>
            <p class="description"> {{note.description}}</p>
        <div class="tags"><button v-for="tag in note.tags" :key="note.slug + tag" @click="selectedTag = tag"> {{tag}}</button></div>
        </li>
        </ul>
    </main>
</template>

<script>
export default {
    async asyncData({ $content}) {
      const notes = await $content("notes")
      .sortBy("updatedOn", "desc").fetch();
      
      return {
          notes
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