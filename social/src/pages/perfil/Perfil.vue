<template>
  <site-template>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="social" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Perfil do usuário</h2>
      <input type="text" placeholder="Nome" v-model="usuario.name">
      <input type="email" placeholder="E-Mail" v-model="usuario.email">

      <div class="file-field input-field">
        <div class="btn">
          <span>Imagem</span>
          <input type="file">
        </div>
        <div class="file-path-wrapper">
          <input class="file-path validate" type="text">
        </div>
      </div>

      <input type="password" placeholder="Senha" v-model="usuario.password">
      <input type="password" placeholder="Confirme sua Senha" v-model="usuario.password_confirmation">
      <button type="button" class="btn waves-effect waves-light" v-on:click="perfil()">Atualizar</button>

    </span>

  </site-template>
</template>

<script>
  import SiteTemplate from '@/templates/SiteTemplate'
  import axios from 'axios';

  export default {
    name: 'Perfil',
    data () {
      return {
        usuario:{name:'', email:'', password:'', password_confirmation:''}
      }
    },
    created(){
      let user = sessionStorage.getItem('usuario');
      if(user){
        this.usuario = JSON.parse(user);
        /*this.usuario.name = this.usuario.name;
        this.usuario.email = this.usuario.email;
        this.usuario.password = this.usuario.password;*/
      }
    },
    components:{
      SiteTemplate
    },
    methods:{
      perfil(){
        axios.put('http://127.0.0.1:8000/api/perfil', {
            name: this.usuario.name,
            email: this.usuario.email,
            password: this.usuario.password,
            password_confirmation: this.usuario.password_confirmation
          },{"headers":{"authorization":"Bearer "+this.usuario.token}})
          .then(response => {
            if(response.data.token){
              console.log(response.data);
              sessionStorage.setItem('usuario',JSON.stringify(response.data));
              alert('Dados atualizados com sucesso!');
            }else{
              //console.log('erro de validacao');
              let erros = '';
              for(let erro of Object.values(response.data)){
                erros += erro + ' ';
              }
              alert(erros);
            }
          })
          .catch(e => {
            //this.errors.push(e)
            //console.log(e);
            alert('Não foi possível realizar a operação. Tente novamente mais tarde!')
          })
      }
    }

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
