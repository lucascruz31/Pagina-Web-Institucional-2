<template>
  <v-app id="inspire">
    <v-app-bar app class="text-white" image="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRiZdpadgJMfIkhPvGGWXo_cri-pbMOsZYrAA&s" height="120">
      <v-btn icon="mdi-menu"></v-btn>

      <v-toolbar-title>
        <v-img 
       
      max-width="100px" 
      src="https://comfacor.com.co/newweb/wp-content/uploads/2022/07/MANUAL-CORPORATIVO-COMFACOR.png"
    ></v-img>
      </v-toolbar-title>

      <v-btn icon="mdi-export" to="/"></v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer">
      <v-sheet
        class="pa-4"
        color="grey-lighten-4"
      >
        <v-avatar
          class="mb-4"
          color="solid black"
          size="64"
        image="https://thumbs.dreamstime.com/b/perfil-del-avatar-de-la-graduaci%C3%B3n-del-estudiante-masculino-81937368.jpg"></v-avatar>

        <div>carlos.m@comfacor.edu.co</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-list-item
          v-for="data in links"
          :key="data.icono"
          :prepend-icon="data.icono"
          :title="data.titulo"
          :to="data.enlace"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container
        class="py-8 px-6"
        fluid
      >
        <v-row>
          <v-col
          
            cols="12"
          >
            <v-card>
              <v-list lines="two">
                <v-list-subheader :title="card"></v-list-subheader>
                        <router-view />
                
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const cards = ['Today', 'Yesterday']
  const links = [
    {
		icono : 'mdi-inbox-arrow-down', 
		titulo : 'Estudiante',
		enlace : '/dashboard/overview',

    },
    {
		icono : 'mdi-inbox-arrow-down', 
		titulo : 'Materias',
		enlace : '/dashboard/stats',

    },
    {
		icono : 'mdi-inbox-arrow-down', 
		titulo : 'Matriculas',
		enlace : '/dashboard/matriculas',

    },
  ]

  const drawer = ref(null)
</script>