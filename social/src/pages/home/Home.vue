<template>
  <span>
    <publicar-conteudo-vue />

    <card-conteudo-vue
      perfil="https://materializecss.com/images/yuna.jpg"
      nome="Maria Silva"
      data="02/05/2020 13:20"
    >
      <card-detalhe-vue
        img="https://materializecss.com/images/sample-1.jpg"
        titulo
        txt="I am a very simple card. I am good at containing small bits of information.
        I am convenient because I require little markup to use effectively."
      />
    </card-conteudo-vue>
  </span>
</template>

<script>
import CardConteudoVue from "@/components/social/CardConteudoVue";
import CardDetalheVue from "@/components/social/CardDetalheVue";
import PublicarConteudoVue from "@/components/social/PublicarConteudoVue";

export default {
  name: "Home",
  data() {
    return {
      msg: ""
    };
  },
  components: {
    CardConteudoVue,
    CardDetalheVue,
    PublicarConteudoVue
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
