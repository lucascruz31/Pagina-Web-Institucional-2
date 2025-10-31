<template>
  <div class="page-background">
    <v-row class="mt-3 mb-3">
      <!-- Misión -->
      <v-col cols="12" md="4">
        <v-card class="custom-card">
          <template v-slot:title>
            <div class="card-title-content">
              <v-icon icon="mdi-bullseye" class="card-icon"></v-icon>
              Misión
            </div>
          </template>

          <template v-slot:text>
            Contribuir a la formación integral de los estudiantes, mediante el desarrollo de procesos afectivos, cognitivos y práxicos.
          </template>
        </v-card>
      </v-col>

      <!-- Visión -->
      <v-col cols="12" md="4">
        <v-card class="custom-card">
          <template v-slot:title>
            <div class="card-title-content">
              <v-icon icon="mdi-eye-outline" class="card-icon"></v-icon>
              Visión
            </div>
          </template>

          <template v-slot:text>
            La Institución Educativa Comfacor "Jaime Exbrayat", será reconocida por la formación integral de sus estudiantes y su contribución en el desarrollo del contexto local y regional.
          </template>
        </v-card>
      </v-col>

      <!-- Objetivo general -->
      <v-col cols="12" md="4">
        <v-card class="custom-card">
          <template v-slot:title>
            <div class="card-title-content">
              <v-icon icon="mdi-target" class="card-icon"></v-icon>
              Objetivo General
            </div>
          </template>

          <template v-slot:text>
            Formar académica, social y moralmente a los estudiantes mediante la adquisición responsable de conocimientos, habilidades, destrezas, actitudes y valores necesarios para su formación integral y trascendental.
          </template>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
// No es necesario incluir lógica en este componente
</script>

<style scoped>
.page-background {
  background: linear-gradient(135deg, #e3f2fd 0%, #f5fbff 50%, #ffffff 100%);
  margin: 0;
  padding: 0;
}

.custom-card {
  background: linear-gradient(135deg, #E1F5FE 0%, #FFFFFF 100%) !important;
  border: 2px solid #B3E5FC !important;
  border-radius: 16px !important;
  box-shadow: 0 4px 12px rgba(179, 229, 252, 0.3) !important;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
  height: 100%;
  position: relative;
  overflow: hidden;
}

.custom-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, #4FC3F7, #0288D1, #4FC3F7);
  opacity: 0;
  transition: opacity 0.4s ease;
}

.custom-card:hover::before {
  opacity: 1;
}

.custom-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 25px rgba(179, 229, 252, 0.5) !important;
  border-color: #4FC3F7 !important;
}

:deep(.v-card-title) {
  color: #01579B !important;
  font-weight: 700 !important;
  font-size: 1.25rem !important;
  padding: 20px 20px 8px !important;
  transition: color 0.3s ease !important;
}

.custom-card:hover :deep(.v-card-title) {
  color: #0288D1 !important;
}

:deep(.v-card-text) {
  color: #0277BD !important;
  line-height: 1.6;
  font-size: 1rem;
  padding: 0 20px 20px !important;
  transition: color 0.3s ease;
}

.custom-card:hover :deep(.v-card-text) {
  color: #01579B !important;
}

.card-title-content {
  display: flex;
  align-items: center;
  gap: 8px;
}

.card-icon {
  color: #0288D1 !important;
  font-size: 1.5rem;
  transition: transform 0.3s ease;
}

.custom-card:hover .card-icon {
  transform: scale(1.2);
  color: #01579B !important;
}

/* Animación de entrada */
.custom-card {
  animation: cardEntrance 0.6s ease-out;
}

@keyframes cardEntrance {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive */
@media (max-width: 960px) {
  .custom-card {
    margin-bottom: 20px;
  }
  
  :deep(.v-card-title) {
    font-size: 1.1rem !important;
    padding: 16px 16px 6px !important;
  }
  
  :deep(.v-card-text) {
    padding: 0 16px 16px !important;
    font-size: 0.95rem;
  }
}

@media (max-width: 600px) {
  .page-background {
    padding: 8px 0;
  }
  
  :deep(.v-card-title) {
    font-size: 1rem !important;
    padding: 12px 12px 4px !important;
  }
  
  :deep(.v-card-text) {
    padding: 0 12px 12px !important;
    font-size: 0.9rem;
  }
  
  .card-icon {
    font-size: 1.2rem;
  }
}
</style>

