<template>
    <div class="login-container text-c animated flipInX">
      <h3 class="text-whitesmoke" v-if="!isEditar">A&ntilde;adir</h3>
      <h3 class="text-whitesmoke" v-if="isEditar">Editar: {{tarea.nombre}}</h3>
      <div class="container-content">
        <input type="text" class="form-control my-2" placeholder="Ej: Deplegar en Netlify...." v-model.trim="tarea.nombre" >
        <div class="mt-2 text-left">
          <span class="text-darkyellow">Grupo</span>
          <hr class="bg-white">
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-2" class="form-check-input" v-model="tarea.categorias" value="scaffolding">
            <label for="check-2" class="form-check-label text-whitesmoke">Scaffolding</label>
          </div>   
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-3" class="form-check-input" v-model="tarea.categorias" value="dependencias">
            <label for="check-3" class="form-check-label text-whitesmoke">Dependencias</label>
          </div>  
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-4" class="form-check-input" v-model="tarea.categorias" value="servicios">
            <label for="check-4" class="form-check-label text-whitesmoke">Servicios</label>
          </div>    
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-5" class="form-check-input" v-model="tarea.categorias" value="bb dd">
            <label for="check-5" class="form-check-label text-whitesmoke">BB.DD</label>
          </div>   
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-6" class="form-check-input" v-model="tarea.categorias" value="maquetacion">
            <label for="check-6" class="form-check-label text-whitesmoke">Maquetaci&oacute;n</label>
          </div>  
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-7" class="form-check-input" v-model="tarea.categorias" value="responsive">
            <label for="check-7" class="form-check-label text-whitesmoke">Responsive</label>
          </div>  
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-8" class="form-check-input" v-model="tarea.categorias" value="testing">
            <label for="check-8" class="form-check-label text-whitesmoke">Testing</label>
          </div>
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-9" class="form-check-input" v-model="tarea.categorias" value="documentacion">
            <label for="check-9" class="form-check-label text-whitesmoke">Documentaci&oacute;n</label>
          </div>   
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-10" class="form-check-input" v-model="tarea.categorias" value="deploy">
            <label for="check-10" class="form-check-label text-whitesmoke">Deploy</label>
          </div>  
          <div class="form-check form-check-inline">
            <input type="checkbox" id="check-11" class="form-check-input" v-model="tarea.categorias" value="hosting">
            <label for="check-11" class="form-check-label text-whitesmoke">Hosting</label>
          </div>                      
        </div>
        <div class="mt-2 text-left">
          <span class="text-darkyellow">Tipo</span>
          <hr class="bg-white"> 
          <div class="form-check form-check-inline">
            <input type="radio" id="radio-1" class="form-check-input" value="urgente" v-model="tarea.estado">
            <label for="radio-1" class="form-check-label text-whitesmoke">Urgente</label>
          </div> 
          <div class="form-check form-check-inline">
            <input type="radio" id="radio-2" class="form-check-input" value="media" v-model="tarea.estado">
            <label for="radio-2" class="form-check-label text-whitesmoke">Media</label>
          </div>  
          <div class="form-check form-check-inline">
            <input type="radio" id="radio-3" class="form-check-input" value="relax" v-model="tarea.estado">
            <label for="radio-3" class="form-check-label text-whitesmoke">Relax</label>
          </div>             
        </div>
        <div class="mt-2 text-left">
          <span class="text-darkyellow">Tiempo</span>
          <hr class="bg-white"> 
          <div class="form-check form-check-inline">
            <label for="horas-1" class="form-check-label text-whitesmoke m-2">Horas</label>
            <input type="number" id="horas-1" class="form-control my-2 w-25" v-model.number="tarea.numero">
          </div> 
        </div>
        <div class="mt-2">
          <button class="form-button button-l margin-b" type="submit" :disabled="bloquear" v-if="!isEditar">A&ntilde;adir</button>  
          <div class="row">
            <div class="col">
              <button class="form-button button-l margin-b" type="submit" :disabled="bloquear" v-if="isEditar">Modificar</button> 
            </div>
            <div class="col">
                <button to="/" class="form-button button-l margin-b" :disabled="bloquear" v-if="isEditar">Cancelar</button>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    props: {
        tarea: Object,
        isEditar: Boolean
    },
    computed: {
        bloquear(){
            return this.tarea.nombre.trim() === "" ? true : false
        }
  }
}
</script>