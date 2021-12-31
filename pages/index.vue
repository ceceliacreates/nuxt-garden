<template>
<div id="app">
  <Navigation />
<main>
  <h1>Cecelia Creates
    </h1>
  <div id="avatar">
  <nuxt-img src="/avatar.png" sizes="sm:80vw md:50vw lg:300px" id="avatar" />
  </div>
  <div id="icons">
  <a href="https://twitter.com/ceceliacreates"><font-awesome-icon :icon="['fab', 'twitter-square']" /></a>
  <a href="https://www.twitch.tv/ceceliacreates"><font-awesome-icon :icon="['fab', 'twitch']" /></a>
  <a href="https://github.com/ceceliacreates"><font-awesome-icon :icon="['fab', 'github-square']" /></a>
  </div>
  <div id="about">
    <h2>Code + content + community. </h2>
    <p>Hi, I'm Cecelia Martinez. 👋 I'm the Developer Community Lead at <a href="https://replay.io">Replay.io</a>, Chapter Head of <a href="https://www.outintech.com">Out in Tech</a> Atlanta, a volunteer with <a href="https://www.womenwhocode.com/frontend" >Women Who Code Front End</a>, and a <a href="https://stars.github.com/">GitHub Star</a>.</p>
    <ul>
      <li> ➡️ Streaming Tuesdays 7:30-9 ET on <a href="https://www.twitch.tv/ceceliacreates">Twitch</a>, coding and answering questions about careers in tech.</li>
      <li> ➡️ Offering free mentoring sessions for underrepresented people getting into tech, follow on <a href="https://twitter.com/ceceliacreates">Twitter</a> for updates</li>
    </ul>
  </div>
  <div class="content">
    <h2> Recent posts </h2>
    <ul>
      <li v-for="article in articles" :key="article.slug + article.createdAt"> <h4>
                <nuxt-link :to="`/articles/${article.slug}`">📄 {{article.title}}
                </nuxt-link>
                </h4>
                <p>{{article.description}}</p>
      </li>
    </ul>
    <p><nuxt-link to="/articles">More...</nuxt-link></p>
    <h2> Recent notes </h2>
    <ul>
      <li v-for="note in notes" :key="note.slug + note.createdAt"> <h4>
                <nuxt-link :to="`/notes/${note.slug}`">✍️ {{note.title}}
                </nuxt-link>
                </h4>
                <p>{{note.description}}</p>
      </li>
    </ul>
    <p><nuxt-link to="/notes">More...</nuxt-link></p>
    </div>
</main>
</div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  async asyncData({ $content}) {
      const articles = await $content("articles")
      .sortBy("publishedOn", "desc").limit(3).fetch();

      const notes = await $content("notes").sortBy("publishedOn", "desc").limit(3).fetch()
      
      return {
          articles, notes
      }
    },
    head: {
    title: "CeceliaCreates.com",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" }
    ]
  }
})
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
}

#avatar {
  border-radius: 25%;
}

#icons {
  display: flex;
  flex-flow: row nowrap;
  justify-content: center;
  gap: .5rem;
  margin: .5rem;
  font-size: 2rem;
}
#about {
  margin: 2rem 4rem;
}
.content {
  text-align: left;
  margin: 1rem 2rem;
}

@media only screen and (max-width: 600px) {
#about {
  margin: 1rem;
}
}

</style>