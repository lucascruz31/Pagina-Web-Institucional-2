<template>
  <div>
    <h2>📊 Mi Plataforma Académica</h2>
    <p>Grado 10° | Colegio Comfacor - Periodo 2024</p>
  </div>  
  <v-container class="pa-6">
    <v-row>
      <v-col cols="12">
        
        <v-divider class="mb-8"></v-divider>

        <v-row dense>
          <v-col 
            v-for="(materia, index) in asignaturas" 
            :key="index" 
            cols="12" 
            sm="6" 
            lg="4"
          >
            <v-card 
              class="mx-auto mb-4" 
              hover
              elevation="4"
              :color="materia.color"
              theme="dark"
            >
              <v-list-item three-line>
                <v-list-item-title class="text-h5 font-weight-bold mb-1">
                  {{ materia.nombre }}
                </v-list-item-title>
                <v-list-item-subtitle>{{ materia.profesor }}</v-list-item-subtitle>
                
                <template v-slot:prepend>
                  <v-avatar size="56">
                    <v-icon size="40">{{ materia.icono }}</v-icon>
                  </v-avatar>
                </template>
              </v-list-item>

              <v-card-text class="py-2">
                <v-list bg-color="transparent" density="compact">
                  <v-list-item prepend-icon="mdi-format-list-bulleted">
                    <v-list-item-title>Unidades: {{ materia.unidades }}</v-list-item-title>
                  </v-list-item>
                  <v-list-item prepend-icon="mdi-calendar-range">
                    <v-list-item-title>Horas Semanales: {{ materia.horas }}</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-card-text>

              <v-card-actions>
                <v-btn variant="elevated" append-icon="mdi-arrow-right" color="white" class="text-dark">
                  Ir al Curso
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>

      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'PlataformaAsignaturas',
  data() {
    return {
      asignaturas: [
        { 
          nombre: 'Matemáticas', 
          profesor: 'Lic. Juan Pérez', 
          icono: 'mdi-calculator-variant',
          unidades: 5,
          horas: 4,
          color: 'blue-darken-2'
        },
        { 
          nombre: 'Física', 
          profesor: 'Ing. Laura Gómez', 
          icono: 'mdi-atom',
          unidades: 4,
          horas: 3,
          color: 'red-darken-3'
        },
        { 
          nombre: 'Lengua Castellana', 
          profesor: 'Mg. Sofía Herrera', 
          icono: 'mdi-book-open-variant',
          unidades: 6,
          horas: 4,
          color: 'green-darken-2'
        },
        { 
          nombre: 'Química', 
          profesor: 'Biól. Andrés Díaz', 
          icono: 'mdi-flask',
          unidades: 4,
          horas: 2,
          color: 'deep-orange-darken-3'
        },
        { 
          nombre: 'Filosofía', 
          profesor: 'Lic. Ernesto Cano', 
          icono: 'mdi-head-lightbulb',
          unidades: 3,
          horas: 2,
          color: 'purple-darken-2'
        },
        { 
          nombre: 'Inglés', 
          profesor: 'Lic. Jennyfer Smith', 
          icono: 'mdi-earth',
          unidades: 5,
          horas: 3,
          color: 'teal-darken-1'
        },
      ]
    }
  }
}
</script>

<style scoped>
.primary--text {
  color: #1976D2 !important; /* Color primario Vuetify */
}
.text-dark {
    color: #1a1a1a !important; /* Para que el texto en el botón resalte sobre el color de la tarjeta oscura */
}
</style>