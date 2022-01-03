---
title: Nuxt Content
publishedOn: 2021-12-24T00:00:00
updatedOn: 2022-01-01T17:34:00
tags: ['vue', 'nuxt', 'project']
description: Nuxt content rebuild project notes
---

## Modules:

- nuxt content
- nuxt image
- nuxtjs/fontawesome

## Steps:

- initiate app
- add content module
- create content directory
- create content markdown files
- use vscode snippet for frontmatter in md files
- create index for each content type
- create _slug page for each content type
- create index page
- add icons
- add navigation
- nuxt routing
- add images: need to research image providers, right now just the one image on homepage
- add style
- layouts for global style
- layouts for dark mode toggle
- MAYBE - Node script to read files in content directory and generate cypress fixture data for testing (???)
- MAYBE - dynamic test that loops through all content files, visits the page based on slug, and asserts the title (???)

```js
const fs = require('fs')
const contentPath = path.join(__dirname, '/../content');

const content = []

fs.readdir(contentPath, (err, files) => {
    if (err) {
        console.log(err)
    }
    else {
        files.forEach( file => {

            // capture the file name as slug
            // read the file and parse the title
            // push the file name and title as an object to content array
            // { slug: 'trimmed filename', title: 'parsed title' }
        })
    }
} )
// write the content array to a fixture file to use with Cypress
```

## Potential Sessions:

### Getting Started
- what is Nuxt
- what is Content Module
- what is Digital Garden
- initiate app
- add content module
- create content directory
- decide on content types
- scaffold content folders
- nuxt md features -- headings, code snippets, components
- what is frontmatter
- create snippet for frontmatter
- create a few content files

### Displaying Content
- creating index page for content type
- fetching content with asyncData()
- parsing frontmatter
- v-for
- adding links
- nuxt routing
- nuxt-link with slug
- creating a slug page to dynamically display content
- fetching a single content file based on slug
- nuxt-content component
- in-browser content editor feature
- repeat process for other content types

### Style and Ship
- content for index page
- adding icons
- adding navigation
- adding style
- layouts for global style
- scoped for local style
- adding cypress tests
- adding data-cy attributes
- dynamic testing for all pages (???)
- what is ssg
- nuxt build process
- connecting to netlify
- merging to main in github automatically deploys to netlify
