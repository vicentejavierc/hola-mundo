<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>


<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script setup>
</script>



<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

/* Estilos del botón */
.login-form button {
  width: 100%;
  padding: 10px;
  background-color: #000;
  color: #fff;
  border: none;
  border-radius: 40px;
  cursor: pointer;
}
</style>




