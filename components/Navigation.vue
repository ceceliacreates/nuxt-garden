<template>
    <nav>
         <button class="nav"><nuxt-link to="/">Home</nuxt-link></button>
        <button class="nav"><nuxt-link to="/articles">Articles</nuxt-link></button>
        <button class="nav"><nuxt-link to="/notes">Notes</nuxt-link></button>
    </nav>
</template>
<script>
export default {
  name: 'Navigation'
}
</script>

<style scoped>
nav {
    font-family: Helvetica, sans-serif;
    text-align: right;
}
a, a:visited, a:hover, a:visited:hover {
  color: white;
  text-decoration: none;
  font-weight: bold;
}


button {
    background-color: #215F5D;
    color: white;
    border: none;
    border-radius: 10%;
    padding: .5rem;
}
button:hover {
    background-color: #6DCCAB;
}
</style>