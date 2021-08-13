<template>
  <NewGame v-if="!startGame" @newGame="newGame" />
  <div class="game" v-else>
    <SecretWord :visualWord="visualWord" />
    <InputWord v-if="!gameOver"
      @findLetter="findLetter($event)"
      @showSecret="showSecret($event)"/>
    <GameOver v-else @newGame="newGame"/>
    <FoundLetter :used="letterUsed" />
    <Life :life="life" />
  </div>
</template>

<script>
import NewGame from "./components/NewGame.vue";
import SecretWord from "./components/SecretWord.vue";
import InputWord from "./components/InputWord.vue";
import FoundLetter from "./components/LetterUsed.vue";
import Life from "./components/Life.vue";
import GameOver from "./components/GameOver.vue"

export default {
  components: { NewGame, SecretWord, InputWord, FoundLetter, Life, GameOver },
  data() {
    return {
      gameOver: false,
      life: 0,
      secretWord: "",
      secretWordAccent: "",
      visualWord: [],
      startGame: false,
      letterUsed: [],
    };
  },
  methods: {
    newGame() {
      let found = false
      const dbWord = [
        "Afobado",
        "Amendoim",
        "Banheiro",
        "Caatinga",
        "Cachorro",
        "Campeonato",
        "Capricórnio",
        "Catapora",
        "Corrupção",
        "Crepúsculo",
        "Empenhado",
        "Esparadrapo",
        "Forca",
        "Galáxia",
        "História",
        "Magenta",
        "Manjericão",
        "Menta",
        "Moeda",
        "Oração",
        "Paçoca",
        "Palavra",
        "Pedreiro",
        "Pneumonia",
        "Pulmão",
        "Rotatória",
        "Serenata",
        "Transeunte",
        "Trilogia",
        "Xícara",
        "Tua Mãe",
      ];
      this.life = 3
      this.gameOver = false
      this.letterUsed = []
      this.visualWord = []
      this.secretWord = dbWord[Math.floor(Math.random() * dbWord.length)]
      this.secretWordAccent = ""
      this.startGame = true
      for (let i = 0; i < this.secretWord.length; i++) {
        const comAcento = "ÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŔÞßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýþÿŕ"
        const semAcento = "AAAAAAACEEEEIIIIDNOOOOOOUUUUYRsBaaaaaaaceeeeiiiionoooooouuuuybyr"
        for (let x = 0; x < comAcento.length; x++) {
          if(this.secretWord[i] == comAcento[x]){
            this.secretWordAccent += semAcento[x]
            found = true
            break
          }else{
            found = false
          }
        }
        found ? null : this.secretWordAccent += this.secretWord[i]
      }

      for (let i = 0; i < this.secretWord.length; i++) {
        this.visualWord.push({ letter: "_", index: i });
      }
    },
    findLetter(letter) {
      let checkFound = false
      if (letter.length) {
        for (let i = 0; i < this.secretWordAccent.length; i++) {
          if (this.secretWordAccent[i].toUpperCase() == letter[0].toUpperCase()) {
            this.visualWord[i].letter = this.secretWord[i]
            checkFound = true
          }
        }
        this.letterUsed.push({ letter: letter[0], found: checkFound })
        !checkFound ? this.life-- : null
        this.gameOver = this.life==0
      }
    },
    showSecret(){
      alert(this.secretWord)
    }
  },
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
}
</style>
