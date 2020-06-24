<template>
  <cadastro-template>
    <div slot="menuesquerdo">
      <img
        src="https://meanstack.com.br/wp-content/uploads/2020/06/social-scaled.jpg"
        class="responsive-img"
        alt="social"
      />
    </div>

    <div slot="principal">
      <h2>Cadastro</h2>

      <input type="text" placeholder="Nome" v-model="name" />
      <input type="text" placeholder="E-mail" v-model="email" />
      <input type="password" placeholder="Senha" v-model="password" />
      <input type="password" placeholder="Confirmar Senha" v-model="password_confirmation" />
      <button type="button" class="btn" v-on:click="cadastro()">Enviar</button>
      <router-link to="/login" class="btn orange">Já possuo conta</router-link>
    </div>
  </cadastro-template>
</template>

<script>
import CadastroTemplate from "@/templates/CadastroTemplate";
import axios from 'axios';

export default {
  name: "Cadastro",
  data() {
    return {
      name:'',
      email:'',
      password:'',
      password_confirmation:''
    };
  },
  components: {
    CadastroTemplate
  },
  methods: {
    cadastro() {
      console.log("Teste");
      axios
        .post(`http://localhost:8000/api/cadastro`, {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.password_confirmation
        })
        .then(response => {
          console.log(response)
          if(response.data.token) {
            // cadastro com sucesso
            console.log('Cadastro realizado com sucesso')
            // localStorage.setItem('usuario', JSON.stringify(response.data));
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
            this.$router.push('/'); // redirect pós cadastro para home
            alert('Cadastro realizado com sucesso!')
          } else if(response.data.status == false) {
            // cadastro não existe
            console.log('Erro no cadastro!')
            alert('Erro no cadastro! Tente novamente mais tarde.')
          } else {
            // erros de validação
            console.log('erros de validação')
            let erros = '';
            for(let erro of Object.values(response.data)) {
              erros += erro + '';
            }
            alert(erros)
          }
        })
        .catch(e => {
          // Erro de servidor
          console.log(e);
          alert('Tivemos um problema. Tente novamente mais tarde.');
        });
    }
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
