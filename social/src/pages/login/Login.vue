<template>
  <login-template>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="social" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Login</h2>
      <input type="email" placeholder="E-Mail" v-model="usuario.email">
      <input type="password" placeholder="Senha" v-model="usuario.password">
      <button class="btn waves-effect waves-light" v-on:click="login()">Entrar</button>
      <router-link to="/cadastro" class="btn orange waves-effect waves-light">Cadastre-se</router-link>

    </span>

  </login-template>
</template>

<script>
  import LoginTemplate from '@/templates/LoginTemplate'
  import axios from 'axios';

  export default {
    name: 'Login',
    data () {
      return {
        usuario:{email:'', password:''}
      }
    },
    components:{
      LoginTemplate
    },
    methods:{
      login(){

        axios.post('http://127.0.0.1:8000/api/login', {
          email: this.usuario.email,
          password: this.usuario.password
        })
        .then(response => {
          console.log(response);
          if(response.data.token){
            //login com sucesso
            console.log('login sucesso');
          }else if(response.data.status == false){
            //login não existe
            console.log('login nao existe');
          }else{
            //errors de validação
            console.log('erro de validacao');
          }
        })
        .catch(e => {
          //this.errors.push(e)
          console.log(e);
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
