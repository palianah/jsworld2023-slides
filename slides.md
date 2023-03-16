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
- Pair Programming with Copilot

<!--
- Werde meine persönlichen Eindrücke zur Konferenz geben
- Dann gabs einen großen Fokus auf Dokumentationstools, da werde ich mal auf ein zwei Libraries eingehen 
- Playwright ist ein E2E Test Framework, das ich bisher nicht benutzt hatte (Cypress in Einsatz), da gab es auch ein cooles   Feature das vorgestellt wurde, indem man sich E2E Tests generieren lassen konnte. Das werde ich mal versuchen Live zu zeigen wie es funktioniert. Ich hab auch mitbekommen das Playwright auch für andere Sprachen kompatibel ist außer nur JS wie z.B Python, Java, and C#
- Dann würde ich gerne nochmal auf Slidev eingehen, da ich das Tool gerade für diese Präsi benutze
-->

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

<!--
- Location war echt super, war im Theater Amsterdam
- Dort gibt es eine sehr große Bühne mit einer riesigen Curved Linewand
- Gutes essen, gab echt immer eine Vielfalt von essen für jeden, war leider immer sehr voll das man lange warten musste, ist aber leider immer so auf Konferenzen
- Echt gute Speakers dabei gewesen. Ich schaue viel auf der Vue Community rum, da sind echt viele gekommen die ich schon mal gehört habe und gute Open Source Projekte geschrieben und aktiv dran arbeiten
- Evan You (Founder von Vue.js), hat auch die Neuigkeiten zu Vue vorgestellt was dieses Jahr kommen wird, wird nochmal ein großes Update dieses Jahr geben, um die Performance nochmal um einiges zu beschleunigen.
- Anthony Fu, den kenn ich auch aus vielen Open Source Projekten, Core Team Member von Vite, Vue
-->

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

<!--
- Da alle Speakers in Open Source Projekten arbeiten, gab es auch viele Talks über Documentationen. 
- Dokumentation schreiben ist sehr wichtig, egal ob Frontend oder Backend
- Merke ich auch immer mehr in meinem Alltag im PLS Projekt, da wir ja quasie im FE auch ein "inner source" Projekt für Mercedes sind und viele unsere Komponente einsetzen, wie wichtig die Dokumentationen sind.
- Vitepress: Markdown Files womit man die Dokumentation aufsetzt, man kann Vue Comoponenten direkt in den Markdown Files benutzen
- Gibt viele vordefinierte Templates womit man sofort mit einem guten UX/UI die Dokumentation aufsetzen kann (natürlich auch custom Templates erstellen)
- Slidev: Nicht wirklich Dokumentationstool, sondern Präsentationstool, aber ähnlich wie Vitepress aufesetzt, mann kann hier auch Vue Componenten und Vite benutzen um die Präsentation zu schreiben
-->

---
transition: fade-out
layout: full
---
# Vitepress

One line install wizard:

```sh [npm]
$ npx vitepress init
```

<br />
<div v-click>
Folder structure looks something like this:
<br /><br />

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
</div>

<!--
- Haben wir neuerlich im PLS Projekt auch neu eingeführt da ich es auf der Konferenz echt cool fand (Wir machen gerade ein komplettes Rewrite von der FE Komponente und dabei schreiben die Doku auch neu)
- Ordnerstruktur sieht so aus: docs Ornder, und dann verschiedene markdown files, mann kann die dokumentation auch auslagern in mehreren md Dateien
- components Ordner um Vue Componenten auszulagern (kann auch inline schreiben)
- wenn man möchte kann man sich auch viele vite lib installieren in der vite.config.ts Datei
-->

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

<!--
- Guter Use-Case um Live Beispiele in der Doku zu zeigen.
- Also das man die Componente die man geschrieben hat hier importiert und z.B mit properties vergibt und der Doku kein Screenshots benutzt sondern die richtige Componente in der Doku sehen kann.
- Beispiel wie mann die Daten aus Vitepress importiert und in der Doku benutzt, also hier z.B das Page Objekt ausgeben wo die aktuelle Page Nummer drin steht bla
-->

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
- E2E Testing Framework
- Generieren von E2E Tests Live zeigen
- aufh für andere Sprachen kompatibel wie z.B Python, Java, and C#
- Let's Code!
- Ich habe ein Beispiel Vorbereitet, die die Mercedes Shop Seite aufmacht. 
- Hier werde ich auf der Hauptseite aufs Profil klicken, versuchen mich einzuloggen und dabei ein Fehler zu machen
- es soll dann auch eine Fehlermeldung angezeigt werden
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


---
transition: fade-out
layout: center
---

# Pair Programming with Copilot!

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
- Einfache Demo um Code etwas schneller zu schreiben
- fühlt sich an als würde man mit AI im pair programmieren :)
-->

---
transition: fade-out
layout: center
---

<style>
.url-container {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-direction: row;
  margin-top: 5px;
}
.url-container img {
  flex: 1 0 auto;
  padding-right: 10px;
}
.url-container a {
  align-self: center;
}
.url li {
  margin-bottom: 20px;
}
</style>

# Demo Code Links
<ul class="url">
  <li>
    presentation url: 
    <div class="url-container">
      <img src="/images/bit.ly_40asObA.png" width="50" />
      <a href="http://bit.ly/40asObA" target="_blank">http://bit.ly/40asObA</a>
    </div>
  </li>
  <li>
    presentation repo: 
     <div class="url-container">
      <img src="/images/bit.ly_3TjDP8h.png" width="50" />
      <a href="http://bit.ly/3TjDP8h" target="_blank">http://bit.ly/3TjDP8h</a>
    </div>
  </li>
  <li>
    playwright demo repo: 
    <div class="url-container">
      <img src="/images/bit.ly_3Jrcb4R.png" width="50" />
      <a href="http://bit.ly/3Jrcb4R" target="_blank">http://bit.ly/3Jrcb4R</a>
    </div>
  </li>
</ul>

<!--
- Hier sind die Links zu den einzelnen Repos die ich für die Präsentation angelegt habe
- Wer Lust hat auch nochmal den Code genauer anzusehen kann sich gerne den QR Code abscannen oder die URL kopieren
-->