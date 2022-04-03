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
      sequence: [],
      hautGauche: false,
      hautDroite: false,
      basGauche: false,
      basDroite: false,
      squareMapping: ["hautGauche", "hautDroite", "basGauche", "basDroite"]
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
  .bleu {
  background-color:blue;
}
.rouge {
  background-color:red;
}
.vert {
  background-color:green;
}
.jaune {
  background-color:yellow;
}
</style>
