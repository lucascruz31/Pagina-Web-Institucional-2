<template>
    <div>
        <v-row class="mt-2 d-flex justify-center login-container">
            <v-col cols="12" md="4" class="fondoimagen">
              <v-card
                    class="mx-auto card-left"
                    elevation="8"
                    rounded="lg"
                    >
              <v-img
                  class="mx-auto logo-img"
                   max-width="200px"
                   src="https://comfacor.com.co/newweb/wp-content/uploads/2022/07/MANUAL-CORPORATIVO-COMFACOR.png"
               ></v-img>
              </v-card>
            </v-col>
            <v-col cols="12" md="7" class="fondo">
                <v-card
                    class="mx-auto card-content"
                    elevation="8"
                    rounded="lg"
                    >
                    <div class="text-subtitle-1 text-medium-emphasis">Account</div>

                    <v-text-field
                        density="compact"
                        placeholder="Email address"
                        prepend-inner-icon="mdi-email-outline"
                        variant="outlined"
                    ></v-text-field>

                    <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
                        Password

                        <a
                        class="text-caption text-decoration-none text-blue"
                        href="#"
                        rel="noopener noreferrer"
                        target="_blank"
                        >
                        Forgot login password?</a>
                    </div>

                    <v-text-field
                        :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                        :type="visible ? 'text' : 'password'"
                        density="compact"
                        placeholder="Enter your password"
                        prepend-inner-icon="mdi-lock-outline"
                        variant="outlined"
                        @click:append-inner="visible = !visible"
                    ></v-text-field>

                    <v-card
                        class="mb-4"
                        color="surface-variant"
                        variant="tonal"
                    >
                        <v-card-text class="text-medium-emphasis text-caption">
                        Warning: After 3 consecutive failed login attempts, you account will be temporarily locked for three hours. If you must login now, you can also click "Forgot login password?" below to reset the login password.
                        </v-card-text>
                    </v-card>

          <v-btn
            class="mb-4"
            color="blue"
            size="large"
            variant="tonal"
            block
            @click="login"
          >
            Log In
          </v-btn>

                    <v-card-text class="text-center">
                        <a
                        class="text-blue text-decoration-none"
                        href="#"
                        rel="noopener noreferrer"
                        target="_blank"
                        >
                        Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
                        </a>
                    </v-card-text>
                    </v-card>

            </v-col>
        </v-row>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const visible = ref(false)
const router = useRouter()

function login() {
  // Aquí podrías validar credenciales antes de navegar.
  // Por ahora simulamos login guardando un flag en localStorage.
  localStorage.setItem('auth', 'true')

  // Si venimos de intentar acceder a una ruta protegida, redirigimos ahí
  let after = null
  try {
    after = JSON.parse(localStorage.getItem('afterLogin') || 'null')
  } catch (e) {
    after = null
  }

  if (after && after.name) {
    router.push(after)
    localStorage.removeItem('afterLogin')
  } else {
    router.push('/dashboard')
  }
}
</script>

<style scoped>
.login-container {
  background: linear-gradient(135deg, #E1F5FE 0%, #FFFFFF 100%);
  min-height: 100vh;
}

.fondoimagen {
  background: linear-gradient(135deg, #4FC3F7, #87CEEB);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.fondo {
  background-color: #FFFFFF;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.card-left {
  background-color: #FFFFFF !important;
  border: 2px solid #B3E5FC;
  padding: 30px 20px;
  min-height: 450px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.card-content {
  background-color: #FFFFFF !important;
  border: 2px solid #B3E5FC;
  padding: 40px 30px;
  min-height: 450px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.logo-img {
  display: block;
  margin: 0 auto;
}

:deep(.v-btn) {
  background: linear-gradient(135deg, #4FC3F7, #87CEEB) !important;
  color: #FFFFFF !important;
}

:deep(.v-field__outline) {
  color: #B3E5FC !important;
}

:deep(.v-field--focused .v-field__outline) {
  color: #4FC3F7 !important;
}

:deep(.v-icon) {
  color: #4FC3F7 !important;
}

:deep(.text-blue) {
  color: #01579B !important;
}

:deep(.v-card[color="surface-variant"]) {
  background-color: #E1F5FE !important;
  border: 1px solid #B3E5FC !important;
}

:deep(.text-medium-emphasis) {
  color: #01579B !important;
}

/* Mejor contraste para textos */
:deep(.v-card-text) {
  color: #333333 !important;
}

:deep(.v-field input) {
  color: #333333 !important;
}

:deep(.v-field .v-label) {
  color: #01579B !important;
}

:deep(.v-card-title) {
  color: #01579B !important;
}

@media (max-width: 960px) {
  .card-left,
  .card-content {
    min-height: 400px;
    padding: 30px 20px;
  }
  
  .logo-img {
    max-width: 180px !important;
  }
}
</style>