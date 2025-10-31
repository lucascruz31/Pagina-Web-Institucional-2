<template>
    <div>
        <h2>🖋️ Matricula del estudiante</h2>
        <p>Inscripcion del estudiante a la institución</p>
    </div>
  <form @submit.prevent="submit">
    <v-text-field
      v-model="name.value.value"
      :counter="50"
      :error-messages="name.errorMessage.value"
      label="Nombre / Apellido"
    ></v-text-field>

    <v-text-field
      v-model="identity.value.value"
      :counter="15"
      :error-messages="identity.errorMessage.value"
      label="Número de Identidad"
    ></v-text-field>

    <v-text-field
      v-model="address.value.value"
      :error-messages="address.errorMessage.value"
      label="Dirección"
    ></v-text-field>

    <v-text-field
      v-model="phone.value.value"
      :counter="7"
      :error-messages="phone.errorMessage.value"
      label="Numero de telefono"
    ></v-text-field>

    <v-text-field
      v-model="email.value.value"
      :error-messages="email.errorMessage.value"
      label="E-mail"
    ></v-text-field>

    <v-select
      v-model="select.value.value"
      :error-messages="select.errorMessage.value"
      :items="items"
      label="Grado"
    ></v-select>

    <v-checkbox
      v-model="checkbox.value.value"
      :error-messages="checkbox.errorMessage.value"
      label="Acepto los términos y condiciones"
      type="checkbox"
      value="1"
    ></v-checkbox>

    <v-btn
      class="me-4"
      type="submit"
    >
      Guardar
    </v-btn>

    <v-btn @click="handleReset">
      Limpiar
    </v-btn>
  </form>
</template>
<script setup>
import { ref } from 'vue'

// Reemplazo ligero de vee-validate para no depender de la librería.
// Conservamos la forma que el template usa: cada campo es un objeto
// con `value` (ref) y `errorMessage` (ref), de modo que las expresiones
// como `name.value.value` y `name.errorMessage.value` sigan funcionando.

const items = ref([
  '6°',
  '7°',
  '8°',
  '9°',
  '10°',
  '11°',
])

const name = { value: ref(''), errorMessage: ref('') }
const identity = { value: ref(''), errorMessage: ref('') }
const address = { value: ref(''), errorMessage: ref('') }
const phone = { value: ref(''), errorMessage: ref('') }
const email = { value: ref(''), errorMessage: ref('') }
const select = { value: ref(null), errorMessage: ref('') }
const checkbox = { value: ref(''), errorMessage: ref('') }

// Reutilizamos las mismas reglas de validación que había en el componente
const validationSchema = {
  name(value) {
    if (value?.length >= 2) return true
    return 'El nombre debe tener al menos 2 caracteres.'
  },
  identity(value) {
    if (/^\d{8,15}$/.test(value)) return true
    return 'El número de identidad debe tener entre 8 y 15 dígitos.'
  },
  address(value) {
    if (value?.length >= 5) return true
    return 'La dirección debe tener al menos 5 caracteres.'
  },
  phone(value) {
    if (/^[0-9-]{7,}$/.test(value)) return true
    return 'El número de teléfono debe tener al menos 7 dígitos.'
  },
  email(value) {
    if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
    return 'Favor ingresar un e-mail válido.'
  },
  select(value) {
    if (value) return true
    return 'Seleccione un grado.'
  },
  checkbox(value) {
    if (value === '1') return true
    return 'Debe aceptar los términos.'
  },
}

function collectValues() {
  return {
    name: name.value.value,
    identity: identity.value.value,
    address: address.value.value,
    phone: phone.value.value,
    email: email.value.value,
    select: select.value.value,
    checkbox: checkbox.value.value,
  }
}

function validateAll() {
  // Resetea mensajes
  name.errorMessage.value = ''
  identity.errorMessage.value = ''
  address.errorMessage.value = ''
  phone.errorMessage.value = ''
  email.errorMessage.value = ''
  select.errorMessage.value = ''
  checkbox.errorMessage.value = ''

  const values = collectValues()
  let valid = true

  for (const key of Object.keys(validationSchema)) {
    const validator = validationSchema[key]
    const result = validator(values[key])
    if (result !== true) {
      valid = false
      // asigna mensaje de error al campo correspondiente
      if (key === 'name') name.errorMessage.value = result
      if (key === 'identity') identity.errorMessage.value = result
      if (key === 'address') address.errorMessage.value = result
      if (key === 'phone') phone.errorMessage.value = result
      if (key === 'email') email.errorMessage.value = result
      if (key === 'select') select.errorMessage.value = result
      if (key === 'checkbox') checkbox.errorMessage.value = result
    }
  }

  return { valid, values }
}

const submit = () => {
  const { valid, values } = validateAll()
  if (valid) {
    // comportamiento original: mostrar los valores
    alert(JSON.stringify(values, null, 2))
  }
}

const handleReset = () => {
  name.value.value = ''
  identity.value.value = ''
  address.value.value = ''
  phone.value.value = ''
  email.value.value = ''
  select.value.value = null
  checkbox.value.value = ''

  name.errorMessage.value = ''
  identity.errorMessage.value = ''
  address.errorMessage.value = ''
  phone.errorMessage.value = ''
  email.errorMessage.value = ''
  select.errorMessage.value = ''
  checkbox.errorMessage.value = ''
}
</script>