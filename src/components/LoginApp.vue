<template>
  <v-app>
    <v-main>
      <v-container fluid class="fill-height">
        <v-row align="center" justify="center">
          <v-col>
            <v-card elevation="0" class="login-card rounded-xl">
              <!-- Header con diseño moderno -->
              <div class="card-header">
                <div class="icon-container">
                  <v-icon size="x-large" color="white">mdi-shield-account</v-icon>
                </div>
                <v-card-title class="text-h4 text-center pa-4 text-white">
                  Iniciar Sesión
                </v-card-title>
                <p class="text-subtitle-1 text-center text-white px-4 pb-4">
                  Accede a tu cuenta para continuar
                </p>
              </div>

              <v-card-text class="pa-6">
                <!-- Alerta de error -->
                <v-alert
                  v-if="error"
                  type="error"
                  variant="tonal"
                  closable
                  class="mb-4 rounded-lg"
                  @click:close="error = ''"
                >
                  {{ error }}
                </v-alert>

                <!-- Alerta de éxito -->
                <v-alert
                  v-if="success"
                  type="success"
                  variant="tonal"
                  class="mb-4 rounded-lg"
                >
                  {{ success }}
                </v-alert>

                <v-form @submit.prevent="handleLogin" ref="form" class="mt-2">
                  <!-- Campo de usuario -->
                  <v-text-field
                    v-model="username"
                    label="Usuario"
                    prepend-inner-icon="mdi-account-outline"
                    variant="outlined"
                    density="comfortable"
                    :rules="[rules.required]"
                    class="mb-4"
                    :disabled="loading"
                    bg-color="white"
                    color="primary"
                  />

                  <!-- Campo de contraseña -->
                  <v-text-field
                    v-model="password"
                    label="Contraseña"
                    prepend-inner-icon="mdi-lock-outline"
                    :type="showPassword ? 'text' : 'password'"
                    :append-inner-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                    @click:append-inner="showPassword = !showPassword"
                    variant="outlined"
                    density="comfortable"
                    :rules="[rules.required]"
                    :disabled="loading"
                    bg-color="white"
                    color="primary"
                  />

                  <!-- Botón de login -->
                  <v-btn
                    type="submit"
                    color="primary"
                    size="large"
                    block
                    :loading="loading"
                    class="mt-2 login-btn rounded-pill"
                    elevation="2"
                  >
                    <v-icon left class="mr-2">mdi-login</v-icon>
                    Ingresar
                  </v-btn>
                </v-form>

                <!-- Información de usuarios de prueba -->
                <v-divider class="my-6" />
                
                <div class="demo-users text-center">
                  <p class="text-caption text-medium-emphasis mb-3">
                    Usuarios de prueba:
                  </p>
                  <v-chip-group class="justify-center">
                    <v-chip variant="outlined" size="small" color="primary">
                      <strong>admin</strong> / admin123
                    </v-chip>
                    <v-chip variant="outlined" size="small" color="primary">
                      <strong>user</strong> / user123
                    </v-chip>
                    <v-chip variant="outlined" size="small" color="primary">
                      <strong>juan</strong> / juan123
                    </v-chip>
                  </v-chip-group>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import authService from '@/services/authservice'

const router = useRouter()

// Estado del formulario
const username = ref('')
const password = ref('')
const showPassword = ref(false)
const loading = ref(false)
const error = ref('')
const success = ref('')
const form = ref(null)

// Reglas de validación
const rules = {
  required: value => !!value || 'Este campo es requerido'
}

/**
 * Maneja el proceso de login
 */
const handleLogin = async () => {
  // Validar formulario
  const { valid } = await form.value.validate()
  if (!valid) return

  // Limpiar mensajes anteriores
  error.value = ''
  success.value = ''
  loading.value = true

  try {
    // Intentar autenticar
    const result = await authService.login(username.value, password.value)

    if (result.success) {
      success.value = `¡Bienvenido ${result.user.nombre}!`
      
      // Redirigir al dashboard después de 1 segundo
      setTimeout(() => {
        router.push('/dashboard')
      }, 1000)
    } else {
      error.value = result.message
    }
  } catch (err) {
    error.value = 'Error inesperado. Por favor intente nuevamente.'
    console.error('Error en login:', err)
  } finally {
    loading.value = false
  }
}
</script>

<style scoped>
.fill-height {
  min-height: 100vh;
  background: linear-gradient(135deg, #E3F2FD 0%, #BBDEFB 50%, #90CAF9 100%);
}

.login-card {
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(33, 150, 243, 0.15) !important;
  border: 1px solid rgba(255, 255, 255, 0.5);
}

.card-header {
  background: linear-gradient(135deg, #42A5F5 0%, #1976D2 100%);
  position: relative;
  overflow: hidden;
}

.card-header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%232196F3' fill-opacity='0.1' fill-rule='evenodd'/%3E%3C/svg%3E");
  opacity: 0.3;
}

.icon-container {
  display: flex;
  justify-content: center;
  padding-top: 24px;
}

.icon-container .v-icon {
  background: rgba(255, 255, 255, 0.2);
  padding: 16px;
  border-radius: 50%;
  backdrop-filter: blur(10px);
}

.login-btn {
  background: linear-gradient(135deg, #42A5F5 0%, #1976D2 100%);
  color: white;
  font-weight: 600;
  letter-spacing: 0.5px;
  height: 48px;
  text-transform: none;
}

.login-btn:hover {
  box-shadow: 0 5px 15px rgba(33, 150, 243, 0.4);
  transform: translateY(-2px);
  transition: all 0.3s ease;
}

:deep(.v-text-field .v-field) {
  border-radius: 12px;
}

:deep(.v-field--outlined) {
  --v-field-border-opacity: 0.3;
}

:deep(.v-chip) {
  border-radius: 8px;
}

.demo-users {
  background-color: #f8fbff;
  border-radius: 12px;
  padding: 12px;
}

/* Efectos de transición suaves */
.v-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.v-card:hover {
  transform: translateY(-5px);
}
</style>