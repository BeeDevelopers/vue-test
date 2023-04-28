<script setup>
import { ref, onUpdated, onBeforeMount } from 'vue'

//PascalCase -> nombrar componentes PascalCase
import ButtonCounter from '@/components/ButtonCounter.vue'

// import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'

const title = 'Memo'
const link = 'https://beedevelopers.dev/'
const test = true
// v-bind or : enlazar variables
// v-on or @ llamadar metodos

//Declarar variables reactivas en Vue 3
//Se tienen que declarar con const
// ref(valor inicial, puede ser null o undefined) para tipo de datos sencillos
// Para modificar el valor de una variable reactiva declarada con ref, se uas .value
// reactive() para objetos complejos

const counter = ref(0)
const btn = ref('Titulo de button')

const counterEmited = (n) => {
  console.log(n)
  counter.value++
}

onBeforeMount(() => {
  console.log('here')
})

onUpdated(() => {
  btn.value = `Titulo de button ${counter.value}`
})
</script>

<template>
  <div>
    <!-- interpolacion de texto -->
    <h1>{{ title }}</h1>

    <!-- enlazar una variables a una etiqueta -->
    <a :href="link" target="_blank">link</a>
    <div :class="{ test: test }">hola</div>

    <!-- Renderiza un elemento en el DOM pero lo oculta -->
    <div v-show="test">Renderizado</div>

    <!-- No renderiza -->
    <div v-if="test">Renderizado</div>
    <div v-else>No</div>

    <div v-for="i in 7" :key="i">
      {{ i }}
    </div>

    {{ counter }}
    <ButtonCounter descr="clickeame!" @counter="counterEmited"></ButtonCounter>
    <ButtonCounter :descr="btn" @counter="counterEmited"></ButtonCounter>
  </div>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">{{ title.toUpperCase() }}</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
</template>

<style scoped>
.test {
  color: red;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
