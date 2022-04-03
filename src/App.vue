<template>
  <div id="app">
    <button @click="newGame">New Game</button>
    <span>Score : {}</span>
    <div>
      <span class="carre" @click="selectSquare('topLeft')" :class="{blue:topLeft}"></span>
      <span class="carre" @click="selectSquare('topRight')" :class="{red:topRight}"></span>
    </div>
    <div>
      <span class="carre" @click="selectSquare('bottomLeft')" :class="{green:bottomLeft}"></span>
      <span class="carre" @click="selectSquare('bottomRight')" :class="{yellow:bottomRight}"></span>
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
      squareMapping: ["topLeft", "topRight", "bottomLeft", "bottomRight"],
      tmp:[]
    }
  },
  methods:{
    newGame() {
      this.sequence=[];
      this.nextTurn();
    },
    addNewElemToSequence() {
      this.sequence.push(this.squareMapping[Math.floor(Math.random() * 4)])
      this.tmp=[...this.sequence]      
    },
    allReset(){
      this.topLeft= false,
      this.topRight=false,
      this.bottomLeft=false,
      this.bottomRight=false
    },
    selectSquare(element){
      if(element === this.tmp[0]){
        console.log('ok')
      } else {
        console.log('pas bon')
      }
    },
    playSequence(element){
      this[element]= true;
      setTimeout(() => {
          this.allReset()
          this.tmp.shift()
          if(this.tmp[0]){
            this.playSequence(this.tmp[0])
          }else{
            this.tmp=[...this.sequence]
          }
      }, 450)
    },
    nextTurn(){
      this.addNewElemToSequence()
      this.allReset()
      this.playSequence(this.tmp[0])
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
