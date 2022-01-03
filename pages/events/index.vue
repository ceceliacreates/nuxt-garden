<template>
    <main>
        <h1>Events</h1>
        <p v-if="selectedTag" class="filter"> Filtered by: {{selectedTag}}  <button @click="selectedTag = ''">Clear</button></p>
        <p v-else class="filter"> Click any tag to filter.</p>
        <ul>
            <li v-for="event in displayedEvents" :key="event.slug + event.createdAt"> <h2>
                <nuxt-link :to="`/events/${event.slug}`">{{event.title}}
                </nuxt-link>
                </h2>
                <h4 v-show="event.org">{{event.org}}</h4>
            <p>{{event.type + ", " + new Date(event.date).toDateString() }}</p>
            <p class="description"> {{event.description}}</p>
        <div class="tags"><button v-for="tag in event.tags" :key="event.slug + tag" @click="selectedTag = tag"> {{tag}}</button></div>
        </li>
        </ul>
    </main>
</template>

<script>
export default {
    async asyncData({ $content}) {
      const events = await $content("events")
      .sortBy("date", "desc").fetch();
      
      return {
          events
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
        displayedEvents() {
            if (this.selectedTag) {
                return this.events.filter(event => event.tags.includes(this.selectedTag))
            } else {
                return this.events
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