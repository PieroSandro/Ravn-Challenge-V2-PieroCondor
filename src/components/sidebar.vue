<template>
 
<div id="first">
    
    <ApolloQuery :query="require('../graphql/allPeople.gql')">
      <template v-slot="{result:{loading,error,data}}">
        <div v-if="data">
          <div v-for="person in data.allPeople.people" :key="person.id" class="user-wrapper">
          <div style="cursor:pointer; font-weight:bold;" 
          @click="show_data(person.eyeColor,person.hairColor,person.skinColor,person.birthYear,person.vehicleConnection.vehicles)">
            {{person.name}}
          </div>
          <div>
            {{person.homeworld.name}}
          </div>
      <!--    <div>
            {{person.vehicleConnection.vehicles[0]}}
          </div>-->
         
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
       // console.log('si fffghola '+this.fres);
      // this.fres=planeta;
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
</style>