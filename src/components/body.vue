<template>
 
<div id="second">
    {{eyeColor}}<br>
    {{hairColor}}<br>
    {{skinColor}}<br>
    {{birthYear}}<br>
    {{vehicleConnection}}<br>
  <!-- <li v-for="vehicle in vehicles_array" :key="vehicle">
    {{ vehicle }}
  </li>-->
  <div v-for="vehicle in vehicles_array" :key="vehicle">
    {{ vehicle }}
  </div>
</div>
</template>


<script>
import {bus} from '../main';
export default {
  name: 'Body',
  props:{
    eyeColor:{
      type:String
    },
    hairColor:{
      type:String
    },
    skinColor:{
      type:String
    },
    birthYear:{
      type:String
    },
     vehicleConnection:{
      type:String
    }
  },
  data(){
    return{
      vehicles_array:[],
      incremento:0
    }
  },
  created(){
    bus.$on('mostrarDatos',(data)=>{
      this.eyeColor=data.eyeColor;
      this.hairColor=data.hairColor;
      this.skinColor=data.skinColor;
       this.birthYear=data.birthYear;
      //  this.vehicleConnection=data.vehicleConnection[1].vehicleClass;
       this.vehicleConnection=data.vehicleConnection;
        this.vehicles_array=[];
 for(this.incremento=0;this.incremento<this.vehicleConnection.length;this.incremento++){
            this.vehicles_array.push(this.vehicleConnection[this.incremento].vehicleClass)
          }
          console.log('arreglo vehi: '+this.vehicles_array)
    })
  }
 
}
</script>
<style>
#second {
    overflow: hidden; 
}
</style>