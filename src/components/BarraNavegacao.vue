<template>
  <nav class="navbar navbar-expand-lg navbar-bytebank">
    <!-- <a class="navbar-brand" href="#">ByteBank</a> -->
    <router-link class="navbar-brand" :to="{name: 'home'}">ByteBank</router-link>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <BarraNavegacaoLogin v-if="usuarioLogado" />
      <BarraNavegacaoLogout v-else/>
    </div>
  </nav>
</template>

<script>
import BarraNavegacaoLogin from "./BarraNavegacaoLogin.vue";
import BarraNavegacaoLogout from "./BarraNavegacaoLogout.vue";
import {mapGetters} from 'vuex'

export default {
  components: {
    BarraNavegacaoLogin,
    BarraNavegacaoLogout,
  },

  computed: {
    ...mapGetters(['usuarioLogado'])
  },

};
</script>

<style>
.navbar {
  background: #27ae60;
}
.navbar-bytebank a {
  color: #fff;
}
.navbar-bytebank a:hover {
  color: #000;
}
</style>