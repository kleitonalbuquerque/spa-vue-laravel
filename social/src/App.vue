<template>
  <div id="app">
    <header>
      <nav-bar cor="green darken-1" logo="Social" url="#" />
    </header>

    <main>
      <div class="container">
        <div class="row">
          <grid-vue tamanho="4">Menu</grid-vue>
          <grid-vue tamanho="8">
            <router-view />
          </grid-vue>
        </div>
      </div>
    </main>

    <footer-vue cor="green darken-1" logo="Social" descricao="Descrição do site" ano="2020">
      <li>
        <a class="grey-text text-lighten-3" href="#!">Home</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 2</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 3</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 4</a>
      </li>
    </footer-vue>
  </div>
</template>

<script>
import NavBar from "@/components/layouts/NavBar";
import FooterVue from "@/components/layouts/FooterVue";
import GridVue from "@/components/layouts/GridVue";

export default {
  name: "App",
  components: {
    NavBar,
    FooterVue,
    GridVue
  }
};
</script>

<style>
</style>
