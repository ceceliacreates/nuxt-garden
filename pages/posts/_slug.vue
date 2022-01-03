<template>
    <main>
         <p><nuxt-link to="/posts"> ⬅️ Back to posts </nuxt-link></p>
        <h1> {{post.title}} </h1>
        <p class="date">Last updated: {{new Date(post.updatedOn).toDateString() }}</p>
        <p class="date"> First published: {{new Date(post.publishedOn).toDateString() }}</p>
        <nuxt-content :document="post" />
        </main>
</template>

<script>
export default {
     async asyncData({ $content, route}) {
         const post = await $content(`posts/${route.params.slug}`).fetch();
         
         return {
             post
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