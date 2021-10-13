<template>
  
  <div class="container text-center">
    <div class="container">
  <!--<div class="inscripcion">-->
    
    <v-app>
      <div class="home">
        <img class="logo" alt="logo" src="../assets/MascotasVacunadas.jpg" />
      </div>
      <Formulario></Formulario>
    </v-app>
  </div>
   <Cerrar></Cerrar>
  </div>
</template>

<script>
import Formulario from "../components/Formulario.vue";
import Cerrar from '../components/Cerrar.vue'

export default {
  name: "Inscripcion",
  components: {
    Formulario,
    Cerrar,
  },
};
</script>
<style lang="scss">
</style>