<template>
    <div class="tareas-container text-c animated flipInX">
        <h3 class="text-whitesmoke">Lista de Tareas</h3>
        <div class="container-content">
            <!-- {{tareas}} -->
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col" class="text-darkyellow">Nombre</th>
                        <th scope="col" class="text-darkyellow">Categorias</th>
                        <th scope="col" class="text-darkyellow">Estado</th>
                        <th scope="col" class="text-darkyellow">Tiempo</th>
                        <th scope="col" class="text-darkyellow">Opciones</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in tareas" :key="item.id">
                        <td class="text-whitesmoke">{{item.nombre}}</td>
                        <td class="text-whitesmoke">
                            <span v-for="(cat, index) in item.categorias" :key="index">
                                {{
                                    (item.categorias.length === index + 1) ? cat : cat + ', '
                                }}
                            </span>
                        </td>
                        <td class="text-whitesmoke">{{item.estado}}</td>
                        <td class="text-whitesmoke">{{item.numero}} Hrs.</td>
                        <td>
                            <div class="row">
                                <div class="col">
                                    <button class="form-button button-l margin-b" @click="deleteTareas(item.id)">Eliminar</button>
                                </div>
                                <div class="col">
                                    <router-link :to="{ name: 'Editar', params: { id: item.id } }">
                                         <button class="form-button button-l margin-b">Editar</button>    
                                    </router-link>                                    
                                </div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import {mapState, mapActions} from 'vuex'
export default {
    computed: {
        ...mapState(['tareas'])
    },
    methods: {
        ...mapActions(['deleteTareas'])
    }
}
</script>