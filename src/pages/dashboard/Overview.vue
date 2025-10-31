<template>
  <div class="overview">
    <h2>🧑‍🎓 Mi Ficha Estudiantil</h2>
    <p>Datos personales del estudiante</p>
    
  <v-container class="pa-6">
    <v-row>
      <v-col cols="12" md="10" lg="8">
        
        <v-divider class="mb-6"></v-divider>

        <v-row dense>
          <v-col cols="12" class="mb-4">
            <div class="d-flex align-center">
              <v-icon color="primary" class="mr-3">mdi-account-details-outline</v-icon>
              <div>
                <strong class="text-h6 d-block">Nombre Completo:</strong>
                <span class="text-body-1">{{ estudiante.nombre }} {{ estudiante.apellidos }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>

          <v-col cols="12" sm="6" class="mb-4">
            <div class="d-flex align-center">
              <v-icon color="primary" class="mr-3">mdi-school</v-icon>
              <div>
                <strong class="text-h6 d-block">Grado:</strong>
                <span class="text-body-1">{{ estudiante.grado }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>
          <v-col cols="12" sm="6" class="mb-4">
            <div class="d-flex align-center">
              <v-icon color="primary" class="mr-3">mdi-badge-account-horizontal</v-icon>
              <div>
                <strong class="text-h6 d-block">Nro. de Identidad:</strong>
                <span class="text-body-1">{{ estudiante.identidad }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>

          <v-col cols="12" sm="6" class="mb-4">
            <div class="d-flex align-center">
              <v-icon color="primary" class="mr-3">mdi-phone</v-icon>
              <div>
                <strong class="text-h6 d-block">Teléfono:</strong>
                <span class="text-body-1">{{ estudiante.telefono }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>
          <v-col cols="12" sm="6" class="mb-4">
            <div class="d-flex align-center">
              <v-icon color="primary" class="mr-3">mdi-email</v-icon>
              <div>
                <strong class="text-h6 d-block">Correo Electrónico:</strong>
                <span class="text-body-1">{{ estudiante.correo }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>

          <v-col cols="12" class="mb-4">
            <div class="d-flex align-start">
              <v-icon color="primary" class="mr-3 mt-1">mdi-home</v-icon>
              <div>
                <strong class="text-h6 d-block">Dirección de Residencia:</strong>
                <span class="text-body-1">{{ estudiante.direccion }}</span>
              </div>
            </div>
            <v-divider class="mt-2"></v-divider>
          </v-col>
        </v-row>

        <v-row class="mt-6">
            <v-col cols="12">
                <v-chip color="success" prepend-icon="mdi-check-circle-outline">
                    Registro de Matrícula Verificado
                </v-chip>
            </v-col>
        </v-row>

      </v-col>
    </v-row>
  </v-container>
  </div>
</template>

<script>
export default {
  name: 'DatosEstudianteDirecto',
  data() {
    return {
      estudiante: {
        nombre: 'Carlos Andrés',
        apellidos: 'Mendoza Pérez',
        identidad: '1.111.222.333',
        telefono: '+57 300 123 4567',
        grado: '10° (Décimo)',
        correo: 'carlos.m@comfacor.edu.co',
        direccion: 'Carrera 15 #20-35, Barrio El Recreo, Montería'
      }
    }
  }
}
</script>

<style scoped>
.primary--text {
  /* Usando una variable de Vuetify si está configurada, o un color directo */
  color: #1976D2 !important; 
}
</style>