<script setup lang="ts"></script>
<template>
  <header>
    <nav>
      <RouterLink to="/" class="nav">Home</RouterLink>
      <RouterLink to="/todolist" class="nav">Todolist</RouterLink>
      <RouterLink to="/about" class="nav">About</RouterLink>
    </nav>
  </header>
</template>
<style scoped>
nav {
  text-align: center;
  font-size: xx-large;
}
.nav {
  border: 1px solid;
  color: black;
  padding-left: 10px;
  padding-right: 10px;
  text-decoration: none;
}
</style>
