<template>
  <v-carousel
    height="400"
    show-arrows="hover"
    cycle
    hide-delimiter-background
    class="custom-carousel"
    interval="5000"
    hide-delimiters
  >
    <v-carousel-item
      v-for="(slide, i) in slides"
      :key="i"
      :src="slide"
      cover
      class="carousel-slide"
    />
  </v-carousel>
</template>

<script setup>
const slides = [
  "https://upload.wikimedia.org/wikipedia/commons/6/63/Reyes_catolicos_colegio_bogota.jpg",
  "https://upload.wikimedia.org/wikipedia/commons/1/12/Colegio_Rosa_de_Santa_Mar%C3%ADa_patio_2017.jpg",
  "https://live.staticflickr.com/7748/17369825872_3968dcee76_b.jpg",
]
</script>

<style scoped>
.custom-carousel {
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 12px 30px rgba(179, 229, 252, 0.5);
  border: 3px solid #e3f2fd;
  position: relative;
}

.carousel-slide {
  transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94),
              opacity 0.8s ease-in-out !important;
}

/* Botones de navegación mejorados */
:deep(.v-carousel__prev), 
:deep(.v-carousel__next) {
  background: linear-gradient(135deg, #4FC3F7 0%, #0288D1 100%) !important;
  color: white !important;
  border-radius: 50% !important;
  margin: 0 25px !important;
  width: 60px !important;
  height: 60px !important;
  box-shadow: 0 6px 20px rgba(2, 136, 209, 0.4) !important;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
  border: 2px solid rgba(255, 255, 255, 0.8) !important;
  opacity: 0;
}

:deep(.v-carousel:hover .v-carousel__prev),
:deep(.v-carousel:hover .v-carousel__next) {
  opacity: 0.9;
}

:deep(.v-carousel__prev:hover, .v-carousel__next:hover) {
  background: linear-gradient(135deg, #0288D1 0%, #01579B 100%) !important;
  transform: scale(1.15) translateY(-2px);
  box-shadow: 0 10px 25px rgba(2, 136, 209, 0.6) !important;
  opacity: 1;
}

:deep(.v-carousel__prev) {
  left: 10px !important;
}

:deep(.v-carousel__next) {
  right: 10px !important;
}

/* Ocultar completamente los controles/delimitadores */
:deep(.v-carousel__controls) {
  display: none !important;
}

:deep(.v-img) {
  border-radius: 16px;
  transition: transform 1.2s ease-in-out !important;
}

:deep(.v-carousel__item--active .v-img) {
  transform: scale(1.05);
}

/* Efecto de transición suave entre slides */
:deep(.v-window__container) {
  transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
}

/* Efecto de superposición sutil para mejorar contraste de botones */
:deep(.v-carousel__item::before) {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(2, 119, 189, 0.1) 0%,
    rgba(2, 119, 189, 0.05) 50%,
    transparent 100%
  );
  pointer-events: none;
  border-radius: 16px;
  z-index: 1;
}

:deep(.v-carousel__prev),
:deep(.v-carousel__next) {
  z-index: 2;
}

/* Efecto de brillo al pasar el mouse sobre el carrusel */
.custom-carousel:hover :deep(.v-img) {
  filter: brightness(1.05);
}

/* Responsive */
@media (max-width: 768px) {
  :deep(.v-carousel__prev), 
  :deep(.v-carousel__next) {
    width: 50px !important;
    height: 50px !important;
    margin: 0 15px !important;
  }
}

@media (max-width: 480px) {
  :deep(.v-carousel__prev), 
  :deep(.v-carousel__next) {
    width: 45px !important;
    height: 45px !important;
    margin: 0 10px !important;
  }
}
</style>
