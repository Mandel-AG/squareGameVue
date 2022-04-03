<template>
  <div id="app">
    <button @click="newGame">New Game</button>
    <div>
      <span class="carre" :class="{blue:topLeft}"></span>
      <span class="carre" :class="{red:topRight}"></span>
    </div>
    <div>
      <span class="carre" :class="{green:bottomLeft}"></span>
      <span class="carre" :class="{yellow:bottomRight}"></span>
    </div>
    <pre>{{ sequence }}</pre>
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
  },
  methods:{
    newGame() {
      this.addNewElemToSequence();
    },
    addNewElemToSequence() {
      this.sequence=[];
      this.sequence.push(this.squareMapping[Math.floor(Math.random() * 4)])
      this[this.sequence[0]]= true;
      console.log(this)
      setTimeout(() => {
        this.allReset()
      }, 1000)
    },
    allReset(){
      this.topLeft= false,
      this.topRight=false,
      this.bottomLeft=false,
      this.bottomRight=false
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
