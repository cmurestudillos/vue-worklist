<template>
    <div class="login-container text-c animated flipInX">
        <div>
            <h1 class="logo-badge text-whitesmoke">
                <span class="fa fa-user-circle"></span>
            </h1>
        </div>
        <h3 class="text-whitesmoke">Login de Acceso</h3>
        <div class="container-content">
            <form class="margin-t" @submit.prevent="ingresoUsuario({email:$v.email.$model,password:$v.pass1.$model})">
                <div class="form-group">
                    <input type="email" class="form-control" placeholder="Email" v-model="$v.email.$model">
                    <p class="alert alert-danger" v-for="(error, index) of $v.email.$errors" :key="index">
                        <span v-if="error.$message === 'Value is required' ">Campo requerido</span>
                        <span v-if="error.$message === 'Value is not a valid email address' ">Dirección de correo electrónico no válida.</span>
                    </p>
                </div>
                <div class="form-group">
                    <input type="password" class="form-control" placeholder="Contraseña" v-model="$v.pass1.$model">
                    <p class="alert alert-danger" v-for="(error, index) of $v.pass1.$errors" :key="index">
                        <span v-if="error.$message === 'Value is required' ">Campo requerido</span>
                        <span v-if="error.$message === 'This field should be at least 6 long' ">Password debe tener al menos un minimo de 6 caracteres.</span>
                    </p>
                </div>
                <button class="form-button button-l margin-b" :disabled="$v.$invalid">Ingresar</button>
                <!-- <a class="text-darkyellow" href="#"><small>Forgot your password?</small></a> -->
                <p class="text-whitesmoke text-center">
                    <small class="mr-2">¿Aun no tienes cuenta?</small>
                    <a class="text-darkyellow" href="/registro">
                        <small>Registrate</small>
                    </a>
                </p>
            </form>

            <p class="margin-t text-whitesmoke">
                <small>Copyright &copy; - Designed and Created by:</small>
                <a class="text-darkyellow text-center ml-2" href="#" target="_blank" rel="noopener noreferrer">
                    <small>Carlos Mur</small>
                </a>    
            </p>
            <small class="margin-t text-whitesmoke"><i>Version: {{version}}</i></small>
            <small class="margin-t text-whitesmoke"> / Contacto: 
                <a href="mailto:cmurestudillos@gmail.com?Subject=Interesado%20en%20tu%20aplicacion" class="text-darkyellow h6 mr-1"><span class="fa fa-envelope"></span></a>
                <a href="skype:carlos.mur.estudillos?chat" class="text-darkyellow h6 ml-1"> <i class="fab fa-skype"></i></a>
            </small>
        </div>
    </div>
</template>

<script>
// Propiedades VUEX
import { mapActions } from 'vuex';
// Validacion de formularios - Vuelidate
import useVuelidate from '@vuelidate/core'
import { required, email, minLength } from '@vuelidate/validators';
import packageInfo  from '../../package.json';

export default {
    data() {
        return {
            $v: useVuelidate(),
            email: '',
            pass1: '',
            version: packageInfo.version
        }
    },
    computed:{ },
    methods: {
        ...mapActions(['ingresoUsuario'])
    },
    validations() {
        return {
            email: { required, email },
            pass1: { required, minLength: minLength(6) }
        }
    }  

}
</script>