<template>
  <v-app-bar app :elevation="2" height="150" class="custom-header">
    <template v-slot:prepend>
      <!-- Eliminado el botón de menú -->
    </template>
    
    <v-img 
      class="mx-auto my-6 header-logo" 
      max-width="100px" 
      src="https://comfacor.com.co/newweb/wp-content/uploads/2022/07/MANUAL-CORPORATIVO-COMFACOR.png"
    ></v-img>

    <v-app-bar-title class="header-title">
      <div class="title-content">
        <div class="institution-name">Institución Educativa Comfacor</div>
        <div class="institution-subtitle">"Jaime Exbrayat"</div>
      </div>
    </v-app-bar-title>

    <template v-slot:append>
      <v-btn 
        class="login-btn" 
        @click="dialog = true"
        variant="flat"
      >
        <v-icon icon="mdi-account-circle" class="mr-2"></v-icon>
        Iniciar Sesión
      </v-btn>
    </template>
  </v-app-bar>

  <v-dialog v-model="dialog" width="600px">
    <LoginApp></LoginApp>
  </v-dialog>  
</template>

<script setup>
  import { ref } from 'vue'
  const dialog = ref(false)
</script>

<style scoped>
.custom-header {
  background: linear-gradient(135deg, #e3f2fd 0%, #f5fbff 50%, #ffffff 100%) !important;
  border-bottom: 3px solid #b3e5fc !important;
  box-shadow: 0 4px 20px rgba(179, 229, 252, 0.4) !important;
  position: relative;
  overflow: hidden;
}

.custom-header::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, #4FC3F7, #0288D1, #4FC3F7);
  animation: shimmer 3s ease-in-out infinite;
}

@keyframes shimmer {
  0%, 100% {
    opacity: 0.7;
  }
  50% {
    opacity: 1;
  }
}

.header-logo {
  filter: drop-shadow(0 2px 8px rgba(2, 136, 209, 0.3));
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  z-index: 2;
}

.header-logo:hover {
  transform: scale(1.05) rotate(2deg);
  filter: drop-shadow(0 4px 12px rgba(2, 136, 209, 0.5));
}

.header-title {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
}

.title-content {
  text-align: center;
  padding: 0 20px;
}

.institution-name {
  color: #01579B;
  font-size: 1.5rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 4px;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.institution-subtitle {
  color: #0288D1;
  font-size: 1.1rem;
  font-weight: 500;
  font-style: italic;
  line-height: 1.2;
}

.login-btn {
  background: linear-gradient(135deg, #4FC3F7 0%, #0288D1 100%) !important;
  color: white !important;
  border-radius: 25px !important;
  padding: 10px 20px !important;
  font-weight: 600 !important;
  text-transform: none !important;
  box-shadow: 0 4px 12px rgba(2, 136, 209, 0.3) !important;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) !important;
  border: 2px solid rgba(255, 255, 255, 0.8) !important;
  position: relative;
  overflow: hidden;
  z-index: 2;
}

.login-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  transition: left 0.5s ease;
}

.login-btn:hover::before {
  left: 100%;
}

.login-btn:hover {
  background: linear-gradient(135deg, #0288D1 0%, #01579B 100%) !important;
  transform: translateY(-2px) scale(1.05);
  box-shadow: 0 6px 20px rgba(2, 136, 209, 0.5) !important;
}

.login-btn :deep(.v-icon) {
  transition: transform 0.3s ease !important;
}

.login-btn:hover :deep(.v-icon) {
  transform: scale(1.1);
}

/* Responsive */
@media (max-width: 960px) {
  .header-title {
    display: none;
  }
  
  .header-logo {
    max-width: 90px !important;
  }
  
  .login-btn {
    padding: 8px 16px !important;
    font-size: 0.9rem;
  }
}

@media (max-width: 600px) {
  .custom-header {
    height: 120px !important;
  }
  
  .header-logo {
    max-width: 80px !important;
    margin: 12px auto !important;
  }
  
  .login-btn {
    padding: 6px 12px !important;
    font-size: 0.8rem;
  }
  
  .login-btn :deep(.v-icon) {
    font-size: 18px !important;
    margin-right: 4px !important;
  }
}

@media (max-width: 400px) {
  .header-logo {
    max-width: 70px !important;
  }
  
  .login-btn {
    padding: 5px 10px !important;
    font-size: 0.75rem;
  }
  
  .login-btn :deep(.v-icon) {
    font-size: 16px !important;
    margin-right: 2px !important;
  }
}
</style>