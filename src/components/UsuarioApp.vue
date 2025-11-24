<template>
     <v-form  ref="form" class="mt-3">
                  <!-- Campo de usuario -->
                  <v-text-field
                    v-model="usuario.email"
                    label="Email"
                    prepend-inner-icon="mdi-account"
                    variant="outlined"
                    density="comfortable"
                    class="mb-3"
                    
                  />

                
                  <v-text-field
                    v-model="usuario.nombre"
                    label="Nombre"
                    prepend-inner-icon="mdi-account"
                    variant="outlined"
                    density="comfortable"
                    />

                     <v-text-field
                     v-model="usuario.username"
                    label="User Name"
                    prepend-inner-icon="mdi-account"
                    variant="outlined"
                    density="comfortable"
                    />
                     <v-text-field
                     v-model="usuario.password"
                    label="PassWord"
                    prepend-inner-icon="mdi-lock"
                    variant="outlined"
                    density="comfortable"
                    />

                     <v-select
                      v-model="usuario.rol"
                      :items="items"
        
                      label="Rol"
                      required
                    ></v-select>

               
                  <v-btn
                    type="submit"
                    color="primary"
                    size="large"
                    block
                    @click="crearusuario"
                  
                    class="mt-4"
                  >
                    <v-icon left class="mr-2">mdi-login</v-icon>
                    Guardar
                  </v-btn>
                  
                </v-form>

</template>

<script setup>
import { reactive } from 'vue';
import usuarioservice from '@/services/usuarioservice'

const items = [
    'Admin',
    'Alumno',
    'Docente',
    'Secretaria',
  ]
  const usuario = reactive({
     username : "",
     password : "",
     email : "",
     nombre : "",
     rol : ""

  })

 const crearusuario= async () => {
  const result = await usuarioservice.usuario(usuario)
}
</script>
