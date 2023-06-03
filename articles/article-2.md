# The basics of Vue.js

In dit artikel ga ik het hebben over de basis van Vue.js. In de eerste projectweek van de Minor Web Design & Development die ik op dit moment volg, kon ik ervoor kiezen om iets nieuws te leren. Ik heb ervoor gekozen om voor het eerst met Vue.js te werken. Nu ga ik schrijven over wat ik in die week heb geleerd en wat extra informatie.

## Wat is vue.js?

Vue.js is een modern JavaScript framework. Waarmee je front-end UI’s mee kunt maken. Je kunt er makkelijk mee starten en dan steeds dingen aan toevoegen, om zo een steeds complexere app te bouwen. Met Vue bouw je boven op de standaard HTML, CSS en JavaScript. Het zorgt voor een declarative en component based programming architecture. Components kunnen worden genest, om er zo voor te zorgen dat het bouwen van apps meer modular en herbruikbaar wordt.

Vue.js is open source en is gemaakt door Evan You. Het werd uitgebracht in 2014.

## Core features

De twee core features van Vue zijn Declarative Rendering en Reactivity.

- Declarative Rendering: hiermee kun je HTML-elementen dynamisch genereren op basis van de huidige staat van je JavaScript code. Door de Vue.js template syntax te gebruiken hoef je de DOM niet handmatig te manipuleren met JavaScript. Met deze syntax zorgt Vue ervoor dat wanneer de staat van de JavaScript code verandert het bijbehorende HTML-element automatisch wordt geupdate.
- Ractivity: Hiermee wordt automatisch de huidige toestand van de JavaScript code bijgehouden. De veranderingen worden doorgegeven aan de DOM. Dit zorgt ervoor dat de HTML automatisch wordt ge-update, zonder dat je de DOM handmatig moet aanpassen.

## Single file component

Vue maakt gebruik van een bestand indeling die erg lijkt op die van een HTML bestand. Dit noemen ze single file components. Deze bestanden geef je een naam met daarachter .vue bijvoorbeeld header.vue. In dit bestand komt de gehele logica van het component. De JavaScript, HTML en CSS.

Voorbeeld:

```html
<script>
  export default {
    data() {
      return {
        likes: 0,
      };
    },
  };
</script>

<template>
  <button @click="likes++">Likes: {{ count }}</button>
</template>

<style scoped>
  button {
    font-weight: bold;
    background-color: #145c9e;
  }
</style>
```

## API styles

Er zijn twee verschillende manieren om Vue components te schrijven. Je hebt de Option API en Composition API.

- Option API: Dit is de traditionele manier om een Vue component te definiëren. Deze manier maakt gebruik van opties om eigenschappen en het gedrag van het component te definiëren. Hiervoor maak je gebruik van data, methods en mounted. Deze methode kan soms leiden tot onoverzichtelijke code. Dit komt vooral voor wanneer je componenten groter worden.
- Composition API: Dit is een alternatief op de Option API, het is een nieuwe manier om een component te definiëren en maakt het makkelijker voor de devoloper. In plaats van alle opties in een object te plaatsen maak je hiermee gebruik van individuele functies. De functies kun je daarna samenvoegen om de eigenschappen en het gedrag te definiëren. Hierdoor wordt de code die je schrijft veel duidelijker. Om deze manier van het schrijven van een component moet je aan de `<script>` tag setup toevoegen. Hierdoor weet Vue dat je de Composition API gebruikt.

Voorbeeld:

```html
<script>
  export default {
    data() {
      return {
        count: 0,
      };
    },

    methods: {
      likes() {
        this.count++;
      },
    },

    mounted() {
      console.log(`The likes are ${this.count}.`);
    },
  };
</script>

<template>
  <button @click="likes">Likes: {{ count }}</button>
</template>
```

## Install a Vue project with Vite

In de project week waarin ik voor het eerst met Vue heb gewerkt, heb ik gebruik gemaakt van Vite. Vite is een building tool dat ervoor zorgt dat het makkelijker wordt voor developers om een development enviroment op te zetten. Je kunt makkelijk een Vue project aanmaken via de commandline met npm. Om Vite te gebruiken heb je wel Node.js nodig, als je dit nog niet hebt geïnstalleerd moet je dat eerst doen. Daarna kun je een Vite project installeren door het volgende command in de commandline te typen `npm create vite@latest`, daarna kun je het stappenplan volgen. Kies bij taal voor JavaScript of TypeScript als je dat fijner vindt en dan als framework natuurlijk Vue. Wanneer je al meteen wilt aangeven wat de naam van het project en het template dat je wilt gebruiken moet worden. Kun je de volgende command typen:

Voor npm 6.x:

```bash
npm create vite@latest my-vue-app --template vue
```

Voor npm 7+:

```bash
npm create vite @latest my-vue-app -- --template vue
```

Als je alle stappen hebt doorlopen kun je het project openen in VScode en daar in de terminal npm install invoeren met daarna npm run dev. Nu kun je het project bekijken in localhost.

Voor meer informatie kijk op vitejs.dev/guide

## Begin with your project

Wanneer je je website bekijkt op de localhost zie je dat er al wat opstaat. Dit heeft Vite alvast voor jou neergezet. Ik wilde meteen met mijn eigen ontwerp beginnen en ging daarom meteen verschillende stukken code verwijderen en toevoegen. Op een gegeven moment ben ik weer op de localhost gaan kijken hoe het er uit zou zien en werkt de website niet meer. Dit kwam doordat ik de Vue function waarmee elk project begint had verwijderd. Wat dus belangrijk is om te laten staan in je Vue project is de `import { createApp } from ‘vue’` met `createApp.mount(‘#app’)`. #app moet een id of class zijn waarin alles van Vue in de HTML gezet kan worden. Dit kan oook met `const app = createApp();`. In `createApp(App)` zetten we dus App. Deze App halen we uit een import die we boven aan toevoegen `import App from ‘App.vue’`. Daarna kun je dan de optie met mout doen als volgt `app.mount(‘#app’)`. Dit zorgt ervoor dat de componenten in de HTML worden gezet. Zorg er altijd voor dat de `.mount()` als laatste komt. Wanneer je dit meerder keren wilt doen doe je dat als volgt:

```javascript
const app1 = createApp()
app1.mount(‘#...’)

const app2 = createApp()
app2.mount(‘#...’)
```

Wanneer je meerdere components hebt gemaakt kun je deze bijvoorbeeld in App.vue importeren en plaatsen waar je dat wilt. Als het goed is heb je al je componenten in een mapje met de naam components. Deze importeer je door tussen `<script setup>` en `</script>` `import Menu from ‘./coomponents/menu.vue’`. Om ervoor te zorgen dat hij ook op de website wordt getoond moet je tussen `<template>` en `</template>` de tag `<Menu />` plaatsen. Nu zou je op je website het menu moeten zien. Dit kun je met al je gemaakte components doen.

## Conclusie

In dit artikel heb ik het eerst over verschillende onderwerpen gehad die handig zijn om te weten voordat je aan de slag gaat. Daarna heb ik een kleine uitleg gegeven over hoe je op een makkelijke manier met Vite een Vue project kan opzetten. Met daarbij nog wat handige dingen die ik niet wist toen ik aan mijn eerste Vue project begon.

Ik hoop dat je met dit artikel wat meer te weten bent gekomen over Vue.js en dat je ook op basis van een website hebt kunnen opzetten. Als je nog meer informatie nodig hebt en/of meer wilt leren neem dan een kijkje bij de linkjes in de bronnen.

## Bronnen:

Creating a vue application (no date) Creating a Vue Application | Vue.js. Available at: https://vuejs.org/guide/essentials/application.html (Accessed: May 5, 2023).

Introduction to Vue (no date) Introduction | Vue.js. Available at: https://vuejs.org/guide/introduction.html (Accessed: May 5, 2023).

MozDevNet (no date) Getting started with Vue - Learn Web Development: MDN, Learn web development | MDN. Available at: https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_getting_started (Accessed: May 5, 2023).

Vue.js Explained in 100 Seconds (2020) YouTube. YouTube. Available at: https://www.youtube.com/watch?v=nhBVL41-_Cw (Accessed: May 5, 2023).

VueJS - Overview (no date) Tutorials Point. Available at: https://www.tutorialspoint.com/vuejs/vuejs_overview.htm (Accessed: May 5, 2023).
