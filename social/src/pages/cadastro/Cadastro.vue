<template>
  <cadastro-template>
    <div slot="menuesquerdo">
      <img
        src="https://meanstack.com.br/wp-content/uploads/2020/05/social.jpg"
        class="responsive-img"
        alt="social"
      />
    </div>

    <div slot="principal">
      <h2>Cadastro</h2>

      <input type="text" placeholder="Nome" value />
      <input type="text" placeholder="E-mail" value />
      <input type="password" placeholder="Senha" name id />
      <input type="password" placeholder="Confirmar Senha" name id />
      <button type="button" class="btn">Enviar</button>
      <router-link to="/login" class="btn orange">Já possuo conta</router-link>
    </div>
  </cadastro-template>
</template>

<script>
import CadastroTemplate from "@/templates/CadastroTemplate";

export default {
  name: "Cadastro",
  data() {
    return {};
  },
  components: {
    CadastroTemplate
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
