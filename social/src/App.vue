<template>
  <div id="app">
    <nav-bar cor="green darken-1" logo="Social" url="#" />
    <router-view />
  </div>
</template>

<script>
import NavBar from '@/components/layouts/NavBar'

export default {
  name: "App",
  components: {
    NavBar
  }
};
</script>

<style>
</style>
