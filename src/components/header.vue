<template>
   <nav class="navbar navbar-expand-lg navbar-light fixed-top">
  <div class="container-fluid">
    <a class="navbar-brand" id="titulo" href="#">Ravn Star Wars Registry</a>
    
  </div>
</nav>
</template>


<script>
export default {
  name: 'Header',
 
}
</script>
<style>
.navbar{
    background-color: #121212;
    height:52px;
    padding:0px;
}
.container-fluid{
    padding:0px;
}
#titulo{
    color: #F2F2F2;
    padding:0px;
    margin-left:33px;
    margin-top: 16px;
    margin-bottom: 16px;
    /*left:33px;*/
    /*top:16px;*/
    font-family: 'SF Pro Display';
    font-style: normal;
    font-weight: bold;
    font-size:17px;
    line-height:20px;
}
</style>