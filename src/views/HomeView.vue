<template>
  <div>
    <v-layout :wrap="true">
      <v-flex xs12>
        
          <h1 class='text-center' >API PRECIO DE DOLAR </h1>
        
        <v-card>
         <v-date-picker 
         v-model="fecha"
         full-width
         :min="minimo"
         :max="maximo"
         @change="getDolar(fecha)">
        </v-date-picker>
        </v-card>
        <v-card color="error" dark>
          <v-card-text class="display-1 text-center">
            {{'$'}} {{valor}} 
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
</div>
</template>

<script>
  
  import axios from "axios";

  export default {

    data() {
      return{
        fecha: new Date().toISOString().substr(0,10),
        minimo: '1984',
        maximo: new Date().toISOString().substr(0,10),
        valor: null
      }
    },
    methods:{
      async getDolar(dia){

       
        let arrayFecha = dia.split(['-'])
        let ddmmyy = arrayFecha[2]+'-'+arrayFecha[1]+'-'+arrayFecha[0];
        
        try {

          let datos = await axios.get(`https://mindicador.cl/api/dolar/${ddmmyy}`)

          if (datos.data.serie.length > 0) {
            this.valor = await datos.data.serie[0].valor
          } else {
            this.valor = 'Sin resultado ( No hay valor de dolar ni sabados ni domingos)'
          }

          

          
          
        } catch (error) {
          
         
        }
        finally {

        }
       

        
      }
    },
    created(){
      this.getDolar(this.fecha)
    }
    

    
  }
</script>
