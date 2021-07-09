<template>
  <div class="navbar navbar-dark">
      <router-link to="/" class="navbar-brand" v-if="usuarioAutenticado">
        <img src="assets/logo.png" width="98" height="98" title="Work List Vue.js" alt="Work List Vue.js" class="rounded mx-auto d-block"  />
      </router-link>
      <div class="row">
        <div class="col-sm-2">
          <span class="text-white" v-if="usuarioAutenticado">Hola:</span></div>
        <div class="col-sm-10">
          <span class="text-darkyellow text-center ml-2" v-if="usuarioAutenticado" >
            {{datosUsuario}}
          </span>
          <div class="row pt-1">
            <div class="col-sm-12">
              <button class="form-button button-l margin-b" v-if="usuarioAutenticado" @click="cerrarSesion">
                Cerrar Sesi&oacute;n
              </button>            
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
// Propiedades de VUEX
import { mapActions, mapGetters } from 'vuex';

export default {
  computed:{
    ...mapGetters(['usuarioAutenticado', 'datosUsuario'])
  },
  methods: {
    ...mapActions(['cerrarSesion'])
  }
}
</script>

