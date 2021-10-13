<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="600px">
      <template v-slot:activator="{ on, attrs }">
        <v-btn color="primary" outlined tile text v-bind="attrs" v-on="on">
          Editar
        </v-btn>
      </template>
      <v-card id="card" class="mx-auto" width="550">
      <v-card-text>
        <v-form ref="form" class="mx-5">
          <v-text-field
            v-model="nombre"
            label="Nombre de tu mascota"
            outlined
          ></v-text-field>
          <v-row align="center" class="ma-0" >
            <v-text-field
            v-model="edad"
            label="Años"
            outlined
            ></v-text-field>
            
          </v-row>
          <v-row align="center" class="ma-auto">
              <v-autocomplete
                v-model="tipo"
                
                :items="tipos"
                label="Tipo de mascota"
                outlined
            ></v-autocomplete>
              <v-autocomplete
                v-model="raza"
                :items="razas"
                Mini
                Pincher
                Samoyedo
                Bulldog
                Sin raza
                San Bernardo
                Coccer Spanic
                label="Raza"
                outlined
              ></v-autocomplete>
          </v-row>
          <v-row align="center" class="ma-0">
          <v-switch
            label="Alerta Notificación"
            color="purple"
            v-model="AlertaNotificacion"
          ></v-switch>
          </v-row>
             
      <v-card-actions class="j-center">
        <v-btn color="success" outlined tile text @click="Guardar"> Guardar </v-btn>
        <v-btn color="red" outlined tile text @click="Salir"> Salir </v-btn>
      </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
import axios from "axios";

export default {
    data: () => ({
    dialog: false,
    activePicker: null,
    date: null,
    menu: false,
    tipos: ["Perro", "Gato"],
    razas: [
      "Mini Pincher",
      "Samoyedo",
      "Bulldog",
      "Criollo",
      "Schnauzer",
      "San Bernardo",
      "Coccer Spanic",
      "Siamese",
      "Persa",
      "Birmano",
      "Oriental",
      "Azul Ruso"
    ],
    AlertaNotificacion: true,
    ultimavacuna: "",
    nombre_vacuna: "",
    meses: "",
    }),

    props: {
    id: String,
    tipo: String,
    raza: String,
    nombre: String,
    edad: Number,
    },

    watch: {
      menu (val) {
        val && setTimeout(() => (this.activePicker = 'YEAR'))
      },
    },
    methods: {
        save (date) {
        this.$refs.menu.save(date)
      },
        Salir(){
            this.dialog=false
        },
        Guardar() {
        const datos = {
        nombre_mascota: this.nombre,
        edad_mascota: this.edad,
        meses: this.meses,
        tipo_mascota: this.tipo,
        raza_mascota: this.raza,  
        usuario_id: localStorage.getItem("usuario_id")      
      };
      console.log(datos);
       let url = "https://mascotas-backend.herokuapp.com/mascota/" + this.id
       axios.put(url,datos).then(res =>{
       console.log(res.data)
       //location.reload()
     }).catch(err =>{
       console.log(err)
     })
    this.dialog = false
    },
    },
};
</script>

<style>
</style>