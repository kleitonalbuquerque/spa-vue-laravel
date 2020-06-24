<template>
  <login-template>
    <div slot="menuesquerdo">
      <img
        src="https://meanstack.com.br/wp-content/uploads/2020/06/social-scaled.jpg"
        class="responsive-img"
        alt="social"
      />
    </div>

    <div slot="principal">
      <h2>Login</h2>

      <input type="text" placeholder="E-mail" v-model="email" />
      <input type="password" placeholder="Senha" v-model="password" />
      <button class="btn" v-on:click="login()">Entrar</button>
      <router-link to="/cadastro" class="btn orange">Cadastre-se</router-link>
    </div>
  </login-template>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      // Uma maneira de criar objeto para login
      // usuario: {
      //   email:'',
      //   password:''
      // }
      // outra maneira de passar os dados para login
      email: "",
      password: ""
    };
  },
  components: {
    LoginTemplate
  },
  methods: {
    login() {
      console.log("Teste");
      axios
        .post(`http://localhost:8000/api/login`, {
          email: this.email,
          password: this.password
        })
        .then(response => {
          console.log(response)
          if(response.data.token) {
            // login com sucesso
            console.log('login com sucesso')
            // localStorage.setItem('usuario', JSON.stringify(response.data));
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
            this.$router.push('/'); // redirect pós login para home
          } else if(response.data.status == false) {
            // login não existe
            console.log('login não existe')
            alert('Login inválido!')
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
