<template>
 
<div id="first">
    
    <ApolloQuery :query="require('../graphql/allPeople.gql')">
      <template v-slot="{result:{loading,error,data}}">
        <div v-if="data">
          <div v-for="person in data.allPeople.people" :key="person.id" class="user-wrapper">
          <div class="person_data" 
          @click="show_data(person.eyeColor,person.hairColor,person.skinColor,person.birthYear,person.vehicleConnection.vehicles)">
          <div class="text_left">
           <p class="person_name">
            {{person.name}}
           </p>
           <p class="person_world">
            <template v-if="person.species==null">
           Human
            </template>
            <template v-else>
              {{person.species.name}}
            </template>
          from {{person.homeworld.name}}
           </p>
          </div>
          <div class="icon_right">
            <i class="fas fa-chevron-right arrow_right"></i>
          </div>
          </div>
         
          </div>
        </div>
        <div v-else-if="error">Sin datos</div>
        <div v-else-if="loading">Cargando</div>
        <div v-else>No result1</div>
      </template>
    </ApolloQuery>
</div>
</template>


<script>
import {bus} from '../main';
export default {
  name: 'Sidebar',
 data(){
     return{
         data_object:{},
     }
 },
  methods: {
    show_data(person_eyeColor,person_hairColor,person_skinColor,person_birthYear,person_vehicleConnection_vehicles){
      this.data_object={
          eyeColor:person_eyeColor,
          hairColor:person_hairColor,
          skinColor:person_skinColor,
          birthYear:person_birthYear,
          vehicleConnection:person_vehicleConnection_vehicles
      }
       bus.$emit('mostrarDatos',this.data_object);
    }
  }
}

</script>
<style>

#first {
    width: 350px;
    height:calc(100vh - 52px) !important;
    float:left; 
    border: 1px solid grey;
    overflow-y: auto;
}

#first::-webkit-scrollbar{
    width:7px;
    background:white;
}
#first::-webkit-scrollbar-thumb{
     width:5px;
    background:white;
    border-radius:8px;
}

#first::-webkit-scrollbar:hover{
    width:7px;
    background:grey;
}
#first::-webkit-scrollbar-thumb:hover{
     width:5px;
    background:black;
    border-radius:8px;
}

.person_data{
  height:69px;
  width:349px;
 /* border-style: solid;
  border-width:1px;
  border-color:red;*/
  border-bottom:1px solid rgba(0,0,0,0.1);
  cursor:pointer;
  overflow:hidden;
}

.text_left{
  width:317.59px;
  height:69px;
  float:left;
}

.icon_right{
  overflow:hidden;
  height:69px;
  width:31.41px;
}

.person_name{
  size:17px;
  height:20px;
  color:#333333;
  font-weight:bold;
  margin-bottom:0px;
  text-align:left;
  margin-top:16px;
  margin-left:14.89px;

}

.person_world{
  size:14px;
  height:17px;
  color:#828282;
  font-weight:normal;
  margin-top:0px;
  text-align:left;
  margin-bottom:16px;
  margin-left:14.89px;
}

.fas{
  color:#000000;
  /*width:7.41px;
  height:12px;*/
  font-size:12px;
  margin-left:0px;
  margin-top:30px;
}
</style>