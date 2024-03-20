<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <header>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/menu">Menu</RouterLink>
        <RouterLink to="/book">Book a Table</RouterLink>
      </nav>
    </header>

    <main>
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #474747;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 999;
}

nav {
  display: flex;
  justify-content: center;
  padding: 1rem 0;
}

nav RouterLink {
  margin: 0 1rem;
  font-size: 18px;
  color: #333333;
  text-decoration: none;
}

nav RouterLink.router-link-exact-active {
  color: #007bff;
}
</style>
