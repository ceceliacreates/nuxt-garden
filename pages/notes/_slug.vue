<template>
    <main>
      <div class="header">
         <p><nuxt-link to="/notes"> ⬅️ Back to notes </nuxt-link></p>
        <h1> {{note.title}} </h1>
        <p class="date" v-if="note.updatedOn > note.publishedOn">Last updated: {{new Date(note.updatedOn).toDateString() }}</p>
        <p class="date"> First created: {{new Date(note.publishedOn).toDateString() }}</p>
      </div>
        <nuxt-content :document="note" />
        </main>
</template>

<script>
export default {
     async asyncData({ $content, route}) {
         const note = await $content(`notes/${route.params.slug}`).fetch();
         
         return {
             note
         }
    },
    head: {
    title: "CeceliaCreates.com",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" }
    ]
  }
}
</script>
<style>
.header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
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