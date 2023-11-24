<template>
  <div id="app">
    <button @click="newGame">New Game</button>
    <span>Score : {{ score }}</span>
    <div>
      <span
        class="carre"
        @click="selectSquare('topLeft')"
        :class="{ blue: topLeft }"
      ></span>
      <span
        class="carre"
        @click="selectSquare('topRight')"
        :class="{ red: topRight }"
      ></span>
    </div>
    <div>
      <span
        class="carre"
        @click="selectSquare('bottomLeft')"
        :class="{ green: bottomLeft }"
      ></span>
      <span
        class="carre"
        @click="selectSquare('bottomRight')"
        :class="{ yellow: bottomRight }"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      sequence: [],
      topLeft: false,
      topRight: false,
      bottomLeft: false,
      bottomRight: false,
      squareMapping: ["topLeft", "topRight", "bottomLeft", "bottomRight"],
      tmp: [],
    };
  },
  computed: {
    score() {
      const value = this.sequence.length - 1;
      return value < 0 ? 0 : value;
    },
  },
  methods: {
    newGame() {
      this.sequence = [];
      this.nextTurn();
    },
    addNewElemToSequence() {
      this.sequence.push(this.squareMapping[Math.floor(Math.random() * 4)]);
      this.tmp = [...this.sequence];
    },
    allReset() {
      (this.topLeft = false),
        (this.topRight = false),
        (this.bottomLeft = false),
        (this.bottomRight = false);
    },
    selectSquare(carre) {
      if (carre === this.tmp[0]) {
        this[carre] = true;
        setTimeout(() => {
          this.allReset();
          this.tmp.shift();
          if (!this.tmp[0]) {
            this.nextTurn();
          }
        }, 400);
      } else {
        alert("perdu");
      }
    },
    playSequence(element) {
      this[element] = true;
      setTimeout(() => {
        this.allReset();
        this.tmp.shift();
        if (this.tmp[0]) {
          setTimeout(() => {
            this.playSequence(this.tmp[0]);
          }, 400);
        } else {
          this.tmp = [...this.sequence];
        }
      }, 450);
    },
    nextTurn() {
      this.addNewElemToSequence();
      this.allReset();
      this.playSequence(this.tmp[0]);
    },
  },
};
</script>

<style>
.carre {
  display: inline-block;
  width: 200px;
  height: 200px;
  background-color: #ccc;
  cursor: pointer;
  margin: 1em;
}
.blue {
  background-color: blue;
}
.red {
  background-color: red;
}
.green {
  background-color: green;
}
.yellow {
  background-color: yellow;
}
</style>
