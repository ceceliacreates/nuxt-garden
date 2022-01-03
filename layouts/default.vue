<template>
<div>
  <Navigation />
  <Nuxt />
</div>
</template>

<style>
html {
    font-family: Helvetica, sans-serif;
  background-color: black;
  color:white;
}

a, a:hover, a:visited, a:visited:hover {
    text-decoration: none;
}

a, a:visited {
  color: #00d4ff
}

a:hover, a:visited:hover {
  color: #6dccab
}

h1 {
  font-size: 3rem;
}

.description {
    font-style: italic;
}

.date {
  margin-top: .5rem;
  margin-bottom: .5rem;
  font-style: italic;
}
</style>