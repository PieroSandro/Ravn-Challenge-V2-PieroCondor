<template>
 
<div id="first">
    
    <ApolloQuery :query="require('../graphql/allPeople.gql')">
      <template v-slot="{result:{loading,error,data}}">
        <div v-if="data">
          <div v-for="person in data.allPeople.people" :key="person.id" class="user-wrapper">
          <div>
            {{person.name}}
          </div>
          <div>
            {{person.homeworld.name}}
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
export default {
  name: 'Sidebar',
 
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