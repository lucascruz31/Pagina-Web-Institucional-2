<template>

    <v-data-table>
      :headers="headers"
      :items="usuarios"
      class="elevation-1"
    </v-data-table>  
</template>

<script setup>
import{ref, onMounted } from 'vue'
import usuarioservice from '@/services/usuarioservice'

const headers = (
    { title: 'Nombre', align: 'start', key: 'nombre' },
    { title: 'Email', align: 'start', key: 'email' },
    { title: 'Rol', align: 'start', key: 'rol' },
    { title: 'Acciones', key: 'actions', sortable: false }
)

const usuarios = ref([])

onMounted(async () => {
  const response =  await usuarioservice.alluser()
  usuarios.value = response.data

})

remove(async(id) =>{
    await usuarioservice.delete(id)
})

</script>