<template>
  <div id="app">
    <div>
    <span class="carre"></span>
    <span class="carre"></span>
  </div>
  <div>
    <span class="carre"></span>
    <span class="carre"></span>
  </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      
    }
  }
}
</script>

<style>
  .carre {
    display: inline-block;
    width:200px;
    height:200px;
    background-color:#ccc;
    cursor:pointer;
  }
</style>
