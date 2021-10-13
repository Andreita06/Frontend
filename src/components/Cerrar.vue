<template>
    <div class="contenedor">
        <v-card-actions>
            <v-btn depressed color="error" elevation="2" block @click="cerrarSesion()"
            >CERRAR SESIÓN</v-btn>
        </v-card-actions>
    </div>
</template>

<script>
export default{
    methods:{
        cerrarSesion(){
            window.localStorage.removeItem('autenticacion');
            console.log("sesion cerrada")
            this.$router.push({path: '/'});
        }
    }
}
</script>

<style>
.contenedor {
  margin: 0 auto;
  align-items: center;
  justify-content: center;
  width: 20%;
}
</style>
