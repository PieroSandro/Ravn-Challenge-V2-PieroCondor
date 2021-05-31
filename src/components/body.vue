<template>
 
<div id="second">
  <div id="rec_1">
    <p id="text_1">General Information</p>
  </div>
  <div id="rec_2">
    <label id="text_2">Eye Color</label>
    <label id="data_2">{{eyeColor | capitalize}}</label>
  </div>
  <div id="rec_3">
    <label id="text_3">Hair Color</label>
     <label id="data_3">{{hairColor | capitalize}}</label>
  </div>
  <div id="rec_4">
    <label id="text_4">Skin Color</label>
     <label id="data_4">{{skinColor | capitalize}}</label>
  </div>
  <div id="rec_5">
    <label id="text_5">Birth Year</label>
     <label id="data_5">{{birthYear}}</label>
  </div>
   <div id="rec_6">
    <p id="text_6">Vehicles</p>
  </div>
  <template v-for="vehicle in vehicles_array">
    <div class="rec_7" :key="vehicle">
    <label class="text_7">{{vehicle | capitalize}}</label>
    </div>
  </template>
</div>
</template>


<script>
import {bus} from '../main';
export default {
  name: 'Body',
  filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
},
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
    text-align:center;
    justify-content:center;
    display: inline-block;
}
#rec_1, #rec_6{
  display: inline-block;
  margin: 0 auto;
  width:890px;
  height:60px;
}

#rec_2, #rec_3, #rec_4, #rec_5{
  width:890px;
  height:49px;
  border-bottom:1px solid rgba(0,0,0,0.1);
}
.rec_7{
   width:890px;
  height:49px;
  border-bottom:1px solid rgba(0,0,0,0.1);
}
#text_1, #text_6{
   size:17px;
  height:20px;
  color:#333333;
  font-weight:bold;
  margin-top:32px;
  text-align:left;
  margin-left:16px;
}

#text_2, #text_3, #text_4, #text_5{
  size:17px;
  height:20px;
  color:#828282;
  font-weight:bold;
  margin-top:14px;
  text-align:left;
  margin-left:16px;
  float:left;
}

.text_7{
  size:17px;
  height:20px;
  color:#828282;
  font-weight:bold;
  margin-top:14px;
  text-align:left;
  margin-left:16px;
  float:left;
}

#data_2, #data_3, #data_4, #data_5{
   text-align:right;
   float:right;
   margin-right:16px;
   margin-top:14px;
   size:17px;
   height:20px;
   color:#333333;
   font-weight:bold;
}
</style>