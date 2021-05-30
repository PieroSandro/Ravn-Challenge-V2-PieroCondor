<template>
  <div id="app">
    <div id="upheader"></div>
    <Header/>
     <div id="wrapper">
    <Sidebar/>
    <Body/>
     </div>
    
  </div>
</template>

<script>
import Header from './components/header.vue'
import Sidebar from './components/sidebar.vue'
import Body from './components/body.vue'

export default {
  name: 'App',
  components: {
    Header,
    Sidebar,
    Body
  }
}
</script>

<style>
#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#upheader{
  height:52px;
}

#wrapper{
 width: 100%;
    overflow: hidden; 
}
</style>
