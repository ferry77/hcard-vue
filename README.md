# hCard Builder

Frameworks/Tools used :
  - Foundation site 6 
  - Vue CLI

Components
  - src/components/hcard-form.vue
  - src/components/hcard-preview.vue
  - src/hCardBuilder.vue

The assumption is at later point state will be managed on higher level structure such as using vuex store.
So here hCard components is stateless components, it receives props from the main hCard app (hCardBuilder.vue). It also maintain one directional data flow, any form data mutation is managed by handleFormChange method in hCardBuilder.js

### Installation

You need Node & Npm installed globally:

```sh
$ npm install
```

```sh
$ git clone https://github.com/ferry77/hcard-vue
$ cd hcard-vue
$ npm install
$ npm run dev
```
