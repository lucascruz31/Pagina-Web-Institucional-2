<template>
  <div class="page-background">
    <v-row class="d-flex justify-center mt-10">
      <div class="text-center">
        <h1 class="display-1 font-weight-bold mb-4 title-gradient">Nuestra Historia</h1>
      </div>
    </v-row>
    <v-row class="d-flex justify-center">
      <v-col cols="12" md="8" lg="6">
        <v-timeline align="start" class="custom-timeline">
          <v-timeline-item
            v-for="(year, i) in years"
            :key="i"
            :dot-color="year.color"
            size="small"
          >
            <template v-slot:opposite>
              <div
                class="pt-1 headline font-weight-bold year-badge"
                v-text="year.year"
              ></div>
            </template>
            <div class="timeline-card">
              <h2 class="mt-n1 headline font-weight-light mb-4 timeline-title">
                {{ year.titulo }}
              </h2>
              <div class="timeline-content">
                {{ year.texto }}
              </div>
            </div>
          </v-timeline-item>
        </v-timeline>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
  const years = [
    {
      color: '#4FC3F7',
      year: '(1984 - 1990)',
      titulo: 'Fundación y primeros años',
      texto: 'El Colegio Comfacor fue fundado por la Caja de Compensación Familiar de Córdoba (Comfacor) con el propósito de brindar educación de calidad a los hijos de los afiliados.',
    },
    {
      color: '#29B6F6',
      year: '(1991 - 2000)',
      titulo: 'Crecimiento académico',
      texto: 'Se amplió la cobertura educativa hasta la educación básica secundaria, se implementaron proyectos pedagógicos orientados al desarrollo social y comunitario y el colegio comenzó a ganar reconocimiento local por su calidad educativa.'
    },
    {
      color: '#03A9F4',
      year: '(2001 - 2010)',
      titulo: 'Consolidación institucional',
      texto: 'Se incorporaron nuevas infraestructuras y recursos tecnológicos, se fortalecieron las áreas de ciencias, inglés y competencias ciudadanas y el colegio reafirmó su compromiso con la formación integral bajo los valores de solidaridad, respeto y responsabilidad.',
    },
    {
      color: '#0288D1',
      year: '(2011 - 2020)',
      titulo: 'Innovación educativa',
      texto: 'Se adoptaron metodologías activas e inclusivas que promueven el aprendizaje significativo, se impulsaron programas de educación ambiental, arte y cultura e inició la integración de TIC en el proceso de enseñanza-aprendizaje.',
    },
    {
      color: '#01579B',
      year: '(2021 - Actualidad)',
      titulo: 'Proyección y calidad',
      texto: 'El colegio continúa posicionándose como una institución educativa líder en Córdoba, se fortalecen los programas de formación en valores, bilingüismo y tecnología y su misión sigue centrada en formar ciudadanos competentes, solidarios y comprometidos con el desarrollo social.',
    },
  ]
</script>

<style scoped>
.page-background {
  background: linear-gradient(135deg, #e3f2fd 0%, #f5fbff 50%, #ffffff 100%);
  margin: 0;
  padding: 20px 0;
  min-height: 100vh;
}

.title-gradient {
  background: linear-gradient(135deg, #01579B 0%, #03A9F4 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.custom-timeline {
  padding: 20px 0;
}

.timeline-card {
  background: linear-gradient(135deg, #FFFFFF 0%, #F5FBFF 100%) !important;
  border: 2px solid #B3E5FC !important;
  border-radius: 16px !important;
  padding: 24px !important;
  box-shadow: 0 4px 12px rgba(179, 229, 252, 0.3) !important;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
  position: relative;
  overflow: hidden;
}

.timeline-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, #4FC3F7 0%, #01579B 100%);
  opacity: 0;
  transition: opacity 0.4s ease;
}

.timeline-card:hover::before {
  opacity: 1;
}

.timeline-card:hover {
  transform: translateX(8px) translateY(-4px);
  box-shadow: 0 8px 20px rgba(179, 229, 252, 0.5) !important;
  border-color: #4FC3F7 !important;
}

.timeline-title {
  color: #01579B !important;
  font-weight: 500 !important;
  transition: color 0.3s ease;
}

.timeline-card:hover .timeline-title {
  color: #0288D1 !important;
}

.timeline-content {
  color: #0277BD !important;
  line-height: 1.6;
  font-size: 1rem;
  transition: color 0.3s ease;
}

.timeline-card:hover .timeline-content {
  color: #01579B !important;
}

.year-badge {
  color: #0288D1 !important;
  background: rgba(179, 229, 252, 0.2);
  padding: 8px 16px;
  border-radius: 20px;
  border: 1px solid #B3E5FC;
  transition: all 0.3s ease;
}

.timeline-card:hover ~ .v-timeline-item__opposite .year-badge {
  background: rgba(79, 195, 247, 0.3);
  border-color: #4FC3F7;
  transform: scale(1.05);
}

:deep(.v-timeline-item__dot) {
  box-shadow: 0 0 0 4px #FFFFFF, 0 0 0 8px currentColor !important;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
}

:deep(.v-timeline-item:hover .v-timeline-item__dot) {
  transform: scale(1.2);
  box-shadow: 0 0 0 4px #FFFFFF, 0 0 0 10px currentColor !important;
}

:deep(.v-timeline-divider__before),
:deep(.v-timeline-divider__after) {
  background-color: #B3E5FC !important;
  transition: background-color 0.3s ease;
}

:deep(.v-timeline-item:hover .v-timeline-divider__before),
:deep(.v-timeline-item:hover .v-timeline-divider__after) {
  background-color: #4FC3F7 !important;
}

:deep(.v-timeline-item__body) {
  background: transparent !important;
}

/* Animaciones de entrada */
.timeline-card {
  animation: slideInRight 0.6s ease-out;
}

.year-badge {
  animation: slideInLeft 0.6s ease-out;
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Responsive */
@media (max-width: 960px) {
  :deep(.v-timeline-item:not(:last-child) .v-timeline-item__body) {
    margin-bottom: 24px;
  }
  
  .timeline-card {
    padding: 20px !important;
  }
  
  .timeline-card:hover {
    transform: translateY(-4px);
  }
}

@media (max-width: 600px) {
  .page-background {
    padding: 15px 0;
  }
  
  .timeline-card {
    padding: 16px !important;
  }
  
  .year-badge {
    font-size: 0.9rem !important;
    padding: 6px 12px;
  }
  
  .timeline-title {
    font-size: 1.1rem !important;
  }
  
  .timeline-content {
    font-size: 0.9rem;
  }
}
</style>