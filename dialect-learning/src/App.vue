<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <router-view />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
}

body {
  width: 100%;
  min-height: 100vh;
  background-color: #f5f5f5;
}

a {
  text-decoration: none;
  color: inherit;
}

ul, li {
  list-style: none;
}

.container {
  width: 100%;
  margin: 0 auto;
  padding: 0 15px;
}
</style>
