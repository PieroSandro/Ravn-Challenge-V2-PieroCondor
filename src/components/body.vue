<template>
 
<div id="second">
    {{eyeColor}}<br>
    {{hairColor}}<br>
    {{skinColor}}<br>
    {{birthYear}}
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
    }
  },
  data(){
    return{

    }
  },
  created(){
    bus.$on('mostrarDatos',(data)=>{
      this.eyeColor=data.eyeColor;
      this.hairColor=data.hairColor;
      this.skinColor=data.skinColor;
       this.birthYear=data.birthYear;
    })
  }
 
}
</script>
<style>
#second {
    overflow: hidden; 
}
</style>