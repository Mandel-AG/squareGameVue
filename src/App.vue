<template>
  <div id="app">
    <div>
    <span class="carre" :class="{blue:topLeft}"></span>
    <span class="carre" :class="{red:topRight}"></span>
  </div>
  <div>
    <span class="carre" :class="{green:bottomLeft}"></span>
    <span class="carre" :class="{yellow:bottomRight}"></span>
  </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      sequence: [],
      topLeft: false,
      topRight: false,
      bottomLeft: false,
      bottomRight: false,
      squareMapping: ["topLeft", "topRight", "bottomLeft", "bottomRight"]
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
    margin: 1em;
  }
  .blue {
  background-color:blue;
}
.red {
  background-color:red;
}
.green {
  background-color:green;
}
.yellow {
  background-color:yellow;
}
</style>
