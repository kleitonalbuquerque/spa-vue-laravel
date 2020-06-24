<template>
  <site-template>
    <div slot="menuesquerdo">
      <img
        src="https://meanstack.com.br/wp-content/uploads/2020/06/social-scaled.jpg"
        class="responsive-img"
        alt="social"
      />
    </div>

    <div slot="principal">

      <h2>Perfil</h2>

      <input type="text" placeholder="Nome" v-model="name" >
      <input type="text" placeholder="E-mail" v-model="email" >

      <!-- Imagem do perfil -->
      <div class="file-field input-field">
      <div class="btn">
        <span>Imagem</span>
        <input type="file" v-on:change="salvaImagem()">
      </div>
      <div class="file-path-wrapper">
        <input class="file-path validate" type="text">
      </div>
    </div>

      <input type="password" placeholder="Senha" v-model="password" >
      <input type="password" placeholder="Confirmar Senha" v-model="password_confirmation" >
      <button type="button" class="btn" v-on:click="perfil()">Atualizar</button>
    </div>
  </site-template>
</template>

<script>
import SiteTemplate from "@/templates/SiteTemplate";
import axios from 'axios';

export default {
  name: "Perfil",
  data() {
    return {
      usuario: false,
      name:'',
      email:'',
      password:'',
      password_confirmation:'',
      imagem:''
    };
  },
  created() {
    // Recupera os dados do usuário logado
    let usuarioAux = sessionStorage.getItem('usuario');
    if(usuarioAux) {
      this.usuario = JSON.parse(usuarioAux);
      this.name = this.usuario.name;
      this.email = this.usuario.email;
    }
  },
  components: {
    SiteTemplate
  },
  methods: {
    salvaImagem(e) {
      let arquivo = event.target.files || event.dataTransfer.files;
      if (!arquivo.length) {
        return;
      }

      let reader = new FileReader();
      reader.onloadend = (e) => {
        this.imagem = e.target.result
      };
      reader.readAsDataURL(arquivo[0])


      console.log(this.imagem);
    },
    perfil() {
      // console.log("ok");
      axios
        .put(`http://localhost:8000/api/perfil`, {
          name: this.name,
          email: this.email,
          imagem: this.imagem,
          password: this.password,
          password_confirmation: this.password_confirmation
        }, {"headers":{"authorization":"Bearer "+this.usuario.token}})
        .then(response => {
          if(response.data.token) {
            // login com sucesso
            console.log(response.data);
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
            alert('Perfil atualizado!')
          // }else if(response.data.status == false) {
          //   // login não exite
          //   alert('Erro no cadastro! Tente novamente mais tarde.');
          }else {
            // erros de validação
            console.log('erros de validação')
            let erros = '';
            for(let erro of Object.values(response.data)) {
              erros += erro +" ";
            }
            alert(erros);
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
