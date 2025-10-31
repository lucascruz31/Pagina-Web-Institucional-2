<template>
  <Header_Pagina/>
  <div id="app">
    <!-- Navegación principal -->
    <nav class="navbar">
      <router-link to="/"></router-link>
      <router-link to="/dashboard"></router-link>
    </nav>
  </div>
  <Carrusel_Compo></Carrusel_Compo>
  <InstitucionalApp></InstitucionalApp>
  <History></History>
  <AppFooter></AppFooter>

  <!-- Aquí se renderizan las rutas principales -->
    <router-view />


</template>

<script setup>
  //
</script>

<style>
body{
  background-color: white;
}
</style>


