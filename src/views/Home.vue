<template>
  <div class="row">
    <div class="col-sm-4">
      <form @submit.prevent="procesarFormulario">
        <Input :tarea="tarea" :isEditar="false" />
      </form>
    </div>
    <div class="col-sm-8">
      <ListaTareas />
    </div>
  </div>
</template>

<script>

import Input from '../components/Input'
import ListaTareas from '../components/ListaTareas'
import {mapActions} from 'vuex'
const shortid = require('shortid');

export default {
  name: 'Home',
  components: {
    Input, ListaTareas
  },
  data() {
    return {
      tarea: {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  methods: {
    ...mapActions(['setTareas', 'cargarLocalStorage']),
    procesarFormulario(){
      console.log(this.tarea)
      if(this.tarea.nombre.trim() === ""){
        console.log('Campo vacío')
        return
      }
      console.log('no está vacio')

      // generar id
      this.tarea.id = shortid.generate()
      console.log(this.tarea.id)
      
      // envian los datos
      this.setTareas(this.tarea)

      // limpiar datos
      this.tarea = {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  created(){
    this.cargarLocalStorage()
  }

}
</script>
