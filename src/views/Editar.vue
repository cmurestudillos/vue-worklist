<template>
    <!-- <div class="login-container text-c animated flipInX">
        <h3 class="text-whitesmoke">Editar Tarea: {{tarea.nombre}}</h3>
        <div class="container-content">
            <form  @submit.prevent="updateTarea(tarea)">
                <div class="form-group">
                    <Input :tarea="tarea" />
                </div>
            </form>
        </div>
    </div> -->
  <div class="row">
    <div class="col-sm-4">
      <form @submit.prevent="updateTarea(tarea)">
        <Input :tarea="tarea" :isEditar="true" />
      </form>
    </div>
    <div class="col-sm-8">
      <ListaTareas />
    </div>
  </div>    
</template>

<script>
import {mapState, mapActions} from 'vuex';
import Input from '../components/Input';
import ListaTareas from '../components/ListaTareas'
export default {
    components:{
        Input, ListaTareas
    },
    computed: {
        ...mapState(['tarea'])
    },
    methods: {
        ...mapActions(['setTarea', 'updateTarea'])
    },
    created(){
        this.setTarea(this.$route.params.id)
    }
}
</script>
