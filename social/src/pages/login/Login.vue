<template>
  <login-template>
    <div slot="menuesquerdo">
      <img src="https://www.wsitebrasil.com.br/sig/www/openged/blog/34/000034_5ad4ef1093728_redessociaislogicadigital.jpg" class="responsive-img" alt="social">
    </div>

    <div slot="principal">
      <h2>Login</h2>

      <input type="text" placeholder="E-mail" value />
      <input type="password" placeholder="Senha" name id />
      <button type="button" class="btn">Entrar</button>
    </div>
  </login-template>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";
import CardConteudoVue from "@/components/social/CardConteudoVue";
import CardDetalheVue from "@/components/social/CardDetalheVue";
import PublicarConteudoVue from "@/components/social/PublicarConteudoVue";

export default {
  name: "Login",
  data() {
    return {
      msg: ""
    };
  },
  components: {
    LoginTemplate,
    CardConteudoVue,
    CardDetalheVue,
    PublicarConteudoVue
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* img {
  margin-top: 20px;
  width: 400px;
  height: 300px;
} */
</style>
