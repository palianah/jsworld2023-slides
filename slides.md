---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./images/IMG_7989.jpg
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
# some information about the slides, markdown enabled
info: |
  ## JSWORLD Conference
  2023
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# JSWORLD Amsterdam

08-11. February 2023

<!--
- Da wir hier keine Frontend COP sind, werde ich nicht auf einzelne FE Details gehen
- Werde allgemein interessante Punkte zeigen die ich auf der Konferenz kennengelernt habe
- Ein zwei Sachen werde ich euch auch Live zeigen um die Präsi etwas interaktiv zu halten :)
-->

---
transition: fade-out
layout: center
---

# Agenda

- Personal Impressions
- All about Documentations
- Live Demo Playwright
- Slidev - write presentations with Vue & Vite
- Bonus: Copilot 

---
transition: fade-out
layout: two-cols
clicks: 11
---
# Personal Impressions

<ul>
<v-clicks at="0"><li> 🏠 super location</li></v-clicks>
<v-clicks at="6"><li> 🍔 good catering</li></v-clicks>
<v-clicks at="8"><li> 👍 good speakers</li></v-clicks>
<v-clicks at="9"><li> 💻 open source, open source!</li></v-clicks>
<v-clicks at="10"><li> ❤️ Amsterdam</li></v-clicks>
</ul>

::right::

<!-- ./components/Day1Images.vue -->
<Day1Images :page="3" :clicks="$slidev.nav.clicks" />

<!-- Docs Libraries Page -->

---
transition: fade-out
layout: full
---

# All about Documentations

<ul>
  <li>
    <a href="https://storybook.js.org" target="_blank">Storybook</a> - good to document ui components
  </li>
  <li>
    <a href="https://histoire.dev" target="_blank">Histoire</a> - Write stories to showcase and document your components.
  </li>
  <li>
    <a href="https://vuepress.vuejs.org" target="_blank">VuePress</a> - Vue powered Static Site Generator
  </li>
  <li>
    <a href="https://vitepress.dev" target="_blank">VitePress</a> - Vite & Vue Powered Static Site Generator
  </li>
  <li>
    <a href="https://sli.dev" target="_blank">Slidev</a> - Presentation Slides for Developers
  </li>
</ul>

---
transition: fade-out
layout: full
---
# Vitepress

One line install wizard:

```sh [npm]
$ npx vitepress init
```

Folder structure looks something like this:

```
├─ docs
│  ├─ .vitepress
│  │  └─ config.ts
│  ├─ api-examples.md
│  ├─ markdown-examples.md
│  ├─ index.md
│  ├─ components
│  │  └─ VueComponent.vue
│  └─ vite.config.ts
│  
└─ package.json
```

---
transition: fade-out
layout: full
---

# Use script setup in Vitepress

```html {2|4|all}
<script setup>
import { useData } from 'vitepress'

const { page } = useData()
</script>

<pre>{{ page }}</pre>
```

---
transition: fade-out
layout: full
---

# Using Components

```vue {2|9|all}
<script setup>
import Counter from '../components/Counter.vue'
</script>

# Docs

This is a .md using a counter component

<Counter :count="1" />

## More docs

...
```

<!-- ./components/Counter.vue -->
<Counter :count="1" m="t-4" />

---
transition: fade-out
layout: center
---

# Playwright - Live Demo

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: fade-out
---

# Slidev - write presentations with Vue & Vite

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

