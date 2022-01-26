<template>
  <div class="container">
    <h1>Login</h1>
    <form v-on:submit.prevent="efetuarLogin">
      <div class="form-group">
        <label for="email">E-mail</label>
        <input type="email" class="form-control" v-model="usuario.email" />
      </div>
      <div class="form-group">
        <label for="senha">Senha</label>
        <input type="password" class="form-control" v-model="usuario.senha" />
      </div>
      <p class="alert alert-danger" v-if="mensagemErro">{{ mensagemErro }}</p>

      <button type="submit" class="btn btn-primary">Logar</button>

      <router-link :to="{ name: 'novo.usuario' }"
        >Não possui um cadastro?
      </router-link>
    </form>
    
    <Stepper />
  </div>
</template>

<script>
import Stepper from "../components/Stepper.vue";

export default {
  components: {
    Stepper,
  },

  data() {
    return {
      usuario: {},
      mensagemErro: "",
    };
  },

  methods: {
    efetuarLogin() {
      this.$store
        .dispatch("efetuarLogin", this.usuario)
        .then(() => {
          this.$router.push({ name: "gerentes" });
          this.mensagemErro = "";
        })
        .catch((erro) => {
          if (erro.request.status === 401) {
            this.mensagemErro = "Login ou senha invalidos";
          }
        });
      // this.$http.post("auth/login", this.usuario)
      //   .then((res) => {
      //     console.log(res);
      //     // localStorage.setItem("token", res.data.access_token);
      //     // this.$store.state.token = res.data.access_token
      //     // this.$store.state.token = res.data.user
      //     this.$store.commit('DEFINIR_USUARIO_LOGADO',{
      //       token: res.data.access_token,
      //       usuario:res.data.user
      //     })
      //     this.$router.push({name:'gerentes'})
      //   })
      //   .catch((err) => console.log(err));
    },
  },
};
</script>
