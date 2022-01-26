<template>
  <div class="container">
    <h1>Novo Usuario</h1>
    <form v-on:submit.prevent="enviarFormulario">
      <div class="form-group">
        <label for="nome">Nome</label>
        <input type="text" class="form-control" v-model="usuario.nome" />
      </div>
      <div class="form-group">
        <label for="nome">E-mail</label>
        <input type="email" class="form-control" v-model="usuario.email" />
      </div>
      <div class="form-group">
        <label for="nome">Senha</label>
        <input type="password" class="form-control" v-model="usuario.senha" />
      </div>
      <button class="btn btn-primary">Salvar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      usuario: {
        nome: "",
        senha: "",
        email: "",
      },
    };
  },

  methods: {
    enviarFormulario() {
      this.$http.post("auth/register",this.usuario)
      .then((res) => {
          this.$router.push({ name: "login" });
          console.log(res);
        },
        (err) => console.log(err)
      );
      console.log(this.usuario);
    },
  },
};
</script>