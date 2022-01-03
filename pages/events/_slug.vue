<template>
    <main>
         <p><nuxt-link to="/events"> ⬅️ Back to events </nuxt-link></p>
        <h1> {{event.title}} </h1>
        <p class="date">{{event.type + ", " + new Date(event.date).toDateString() }}</p>
        <a :href="event.link" v-show="event.link" target="blank"><p>Link to Registration</p></a>
        <div v-show="event.embed" id="video">
        <iframe
              width="460"
              height="258"
              :src="`https://www.youtube.com/embed/${event.embed}`"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
            </div>
            <a :href="event.slides" v-show="event.slides" target="blank"><p>Link to Slides</p></a>
        <p> {{event.description}}</p>
        </main>
</template>

<script>
export default {
     async asyncData({ $content, route}) {
         const event = await $content(`events/${route.params.slug}`).fetch();
         
         return {
             event
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
  margin: 1rem 4rem;
}

@media only screen and (max-width: 600px) {
main {
  margin: 1rem;
}
}
</style>