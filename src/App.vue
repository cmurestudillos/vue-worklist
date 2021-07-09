<template>
  <Navbar />
  <div class="container">
    <router-view/>
  </div>
</template>

<script>
  import {mapActions} from 'vuex';
  // componentes
  import Navbar from './components/shared/Navbar';

  export default {
    components: {
      Navbar
    },
    methods:{
      ...mapActions(['cargarLocalStorage'])
    },
    created(){
      this.cargarLocalStorage();
    }
  }
</script>

