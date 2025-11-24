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
/* Layout */
.custom-header {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 8px 20px;
  background: linear-gradient(90deg, #e8f4fb 0%, #ffffff 100%);
  border-bottom: 1px solid rgba(2, 136, 209, 0.12);
  box-shadow: 0 6px 18px rgba(2, 136, 209, 0.06);
  height: auto;
}

.header-logo {
  max-width: 96px;
  width: 96px;
  height: auto;
  border-radius: 8px;
  object-fit: contain;
  transform-origin: center;
  transition: transform 200ms ease, box-shadow 200ms ease;
}

.header-left {
  display: flex;
  align-items: center;
  gap: 12px;
}

.header-title {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

.title-content {
  padding: 0 8px;
}

.institution-name {
  color: #023e6b;
  font-size: 1.15rem;
  font-weight: 700;
  line-height: 1.1;
}

.institution-subtitle {
  color: #0277bd;
  font-size: 0.95rem;
  font-weight: 500;
  font-style: italic;
}

/* Login button */
.login-btn {
  --btn-bg-1: #18a0ff;
  --btn-bg-2: #0277bd;
  background: linear-gradient(135deg, var(--btn-bg-1), var(--btn-bg-2)) !important;
  color: #fff !important;
  border-radius: 999px !important;
  padding: 8px 16px !important;
  font-weight: 600 !important;
  text-transform: none !important;
  box-shadow: 0 6px 18px rgba(2, 119, 189, 0.18) !important;
  transition: transform 160ms ease, box-shadow 160ms ease !important;
}

.login-btn:hover {
  transform: translateY(-2px) !important;
  box-shadow: 0 10px 28px rgba(2, 119, 189, 0.22) !important;
}

.login-btn :deep(.v-icon) {
  margin-right: 6px;
}

/* Small detail shadow bar */
.custom-header::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 4px;
  background: linear-gradient(90deg, rgba(24,160,255,0.18), rgba(2,119,189,0.12));
  pointer-events: none;
}

/* Responsive tweaks */
@media (max-width: 900px) {
  .institution-name { font-size: 1rem; }
  .institution-subtitle { font-size: 0.9rem; }
  .header-logo { max-width: 80px; width: 80px; }
}

@media (max-width: 600px) {
  .custom-header { padding: 8px 12px; }
  .header-title { display: none; }
  .login-btn { padding: 6px 10px !important; }
  .header-logo { max-width: 64px; width: 64px; }
}
</style>