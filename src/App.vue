<script>
export default {
  data() {
    return {
      scoreone: 0,
      scoretwo:0,
      playing: false,
      playerChoice: "",
      computerChoice: "",
      result: "",
      gameOver: false,
      heartchoice:"https://www.pngmart.com/files/15/Black-Heart-Vector-Transparent-PNG.png"
    };
  },
  methods: {
    playGame() {
      const choices = ["https://www.pngkey.com/png/detail/816-8162314_rock-paper-scissors-mickey-mouse-hand-drawing.png", "https://www.kindpng.com/picc/m/18-188236_mickey-mouse-png-mickey-mouse-glove-template-transparent.png", "https://www.nicepng.com/png/detail/816-8161961_paper-icon-mickey-mouse-hand-drawing.png","https://www.pngmart.com/files/15/Black-Heart-Vector-Transparent-PNG.png"];
      this.playerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.computerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.calculateResult();
      this.playing = true;
    },
    calculateResult() {
      if (this.playerChoice === this.computerChoice) {
        this.result = "เสมอ";
      }else if(this.playerChoice === "https://www.pngmart.com/files/15/Black-Heart-Vector-Transparent-PNG.png"){
        this.result = "playerOne WIN";
        this.scoreone += 1;
      }
      else if(this.computerChoice === "https://www.pngmart.com/files/15/Black-Heart-Vector-Transparent-PNG.png"){
        this.result = "playerTwo WIN";
        this.scoretwo += 1;
      }
      else if (
        (this.playerChoice === "https://www.pngkey.com/png/detail/816-8162314_rock-paper-scissors-mickey-mouse-hand-drawing.png" && this.computerChoice === "https://www.nicepng.com/png/detail/816-8161961_paper-icon-mickey-mouse-hand-drawing.png") ||
        (this.playerChoice === "https://www.kindpng.com/picc/m/18-188236_mickey-mouse-png-mickey-mouse-glove-template-transparent.png" && this.computerChoice === "https://www.pngkey.com/png/detail/816-8162314_rock-paper-scissors-mickey-mouse-hand-drawing.png") ||
        (this.playerChoice === "https://www.nicepng.com/png/detail/816-8161961_paper-icon-mickey-mouse-hand-drawing.png" && this.computerChoice === "https://www.kindpng.com/picc/m/18-188236_mickey-mouse-png-mickey-mouse-glove-template-transparent.png")
      ) {
        this.result = "playerOne WIN";
        this.scoreone += 1;
        this.scoretwo += 0;
      } else {
        this.result = "playerTwo WIN";
        this.scoreone += 0;
        this.scoretwo += 1;
      }
    },
    resetGame() {
      this.playing = false;
      this.playerChoice = "";
      this.computerChoice = "";
      this.result = "";
      this.gameOver = false;
    },
  },
};
</script>

<template>
  <div>
    <h1>เป่ายิ๊ง...ฉุบ</h1>
    <p>scoreplayerOne: {{ scoreone }}</p>
    <p>scoreplayerTwo: {{ scoretwo }}</p>
    <button @click="playGame" :disabled="gameOver">เริ่มเล่น</button>
    <button @click="resetGame" :disabled="!playing">เริ่มใหม่</button>
    <div v-if="playing">
      <h2>playerOne: <img :src="playerChoice" alt="player one Choice" class="small-image"></h2>
      <h2>playerTwo: <img :src="computerChoice" alt="player two Choice" class="small-image"></h2>
      <h3>ผล: {{ result }}</h3>
    </div>
  </div>
</template>

<style scoped>
.small-image {
  max-width: 100px;
  max-height: 100px;}
</style>