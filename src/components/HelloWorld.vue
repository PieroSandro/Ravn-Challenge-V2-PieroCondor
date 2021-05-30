<template>
  <div class="hello">
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
/*import gql from 'graphql-tag';*/
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
