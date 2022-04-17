<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <nav class="navbar fixed-top">
      <RouterLink class="navbar-brand" to="/">Home</RouterLink>
      <RouterLink class="navbar-brand" to="/about">About</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style>
#app {
  max-width: 1280px;
  min-width: 80%;
  margin: 80px auto;
  /*padding: 2rem;*/
  /*font-weight: normal;*/
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  display: flex;
  align-items: center;
  padding: 0 10rem;
  width: 80%;
  margin: 0 auto;
  font-size: 18px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  nav {
    text-align: center;
    margin-top: 1rem;
  }
}
</style>
