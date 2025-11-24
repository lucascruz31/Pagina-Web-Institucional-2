<template>
    <div>
        <h2>🖋️ Crear Usuario</h2>
        <p>Ingrese los datos de la persona en los siguientes apartados</p>
    </div>
  <v-app>
    <v-main>
          <v-col>
            <v-card elevation="8" class="rounded-lg">
                <v-card-text>
                <v-form>
                 <UsuarioApp></UsuarioApp>
                 
                </v-form>
                
                <ListadoUsers></ListadoUsers>
                <!-- Información de usuarios de prueba -->
                <v-divider class="my-6" />
                
                <div class="text-caption text-center text-medium-emphasis">
                  <div class="mb-2">Usuarios de prueba:</div>
                  <div><strong>admin</strong> / admin123</div>
                  <div><strong>user</strong> / user123</div>
                  <div><strong>juan</strong> / juan123</div>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import authService from '@/services/authservice'

import UsuarioApp from '@/components/UsuarioApp.vue'

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
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.v-card {
  overflow: hidden;
}
</style>
