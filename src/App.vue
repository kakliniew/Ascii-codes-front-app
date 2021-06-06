<template>
  <img alt="ascii codes logo" src="./assets/logo.png">
  <div v-if="showKeys">
    <h3>Favourite letters</h3>
    <KeysBoard :letters="favBooks" @onClickControlLetterApp="onClickControlLetter" @onClickLetterApp="onClickLetter"></KeysBoard>
    <h3>All letters</h3>
    <KeysBoard :letters="notFavBooks" @onClickControlLetterApp="onClickControlLetter" @onClickLetterApp="onClickLetter"></KeysBoard>
    <TextBox :textValue="textboxText"></TextBox>
  </div>
  <div v-if="!showKeys" class="chartClass">
    <Chart :clickedLetters="clickedLettersFilter"> </Chart>
  </div>
  <button @click="ButtonOnClick" id="showButtons">{{buttonCaption}}</button>
</template>

<script>
import Chart from './components/Chart.vue'
import TextBox from './components/TextBox.vue'
import KeysBoard from './components/KeysBoard.vue'


export default {
  name: 'App',
  components: {KeysBoard, TextBox, Chart},
  methods: {
    ButtonOnClick(){
      this.showKeys = !this.showKeys;
      if (this.showKeys){
        this.buttonCaption = "Display usage graph"
      }else{
        this.buttonCaption = "Show button keys"
      }  
      console.log(this.clickedLettersFilter)
    },
    onClickControlLetter(message){
      message.letter.isFav = !message.letter.isFav;
    },
    onClickLetter(message){
      message.letter.clicked++;
      this.textboxText = this.textboxText + message.letter.letter;
    }
  },
  data(){
    return {
      showKeys: true,
      textboxText: '',
      buttonCaption: "Display usage graph",
      letters: [
              {letter: 'A', asciicode: '65', isFav: false, clicked: 0},
              {letter: 'B', asciicode: '66', isFav: false, clicked: 0},
              {letter: 'C', asciicode: '67', isFav: false, clicked: 0},
              {letter: 'D', asciicode: '68', isFav: false, clicked: 0},
              {letter: 'E', asciicode: '69', isFav: false, clicked: 0},
              {letter: 'F', asciicode: '70', isFav: false, clicked: 0},
              {letter: 'G', asciicode: '71', isFav: false, clicked: 0},
              {letter: 'H', asciicode: '72', isFav: false, clicked: 0},
              {letter: 'I', asciicode: '73', isFav: false, clicked: 0},
              {letter: 'J', asciicode: '74', isFav: false, clicked: 0},
              {letter: 'K', asciicode: '75', isFav: false, clicked: 0},
              {letter: 'L', asciicode: '76', isFav: false, clicked: 0},
              {letter: 'M', asciicode: '77', isFav: false, clicked: 0},
              {letter: 'N', asciicode: '78', isFav: false, clicked: 0},
              {letter: 'O', asciicode: '79', isFav: false, clicked: 0},
              {letter: 'P', asciicode: '80', isFav: false, clicked: 0},
              {letter: 'Q', asciicode: '81', isFav: false, clicked: 0},
              {letter: 'R', asciicode: '82', isFav: false, clicked: 0},
              {letter: 'S', asciicode: '83', isFav: false, clicked: 0},
              {letter: 'T', asciicode: '84', isFav: false, clicked: 0},
              {letter: 'U', asciicode: '85', isFav: false, clicked: 0},
              {letter: 'V', asciicode: '86', isFav: false, clicked: 0},
              {letter: 'W', asciicode: '87', isFav: false, clicked: 0},
              {letter: 'X', asciicode: '88', isFav: false, clicked: 0},
              {letter: 'Y', asciicode: '89', isFav: false, clicked: 0},
              {letter: 'Z', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'a', asciicode: '97', isFav: false, clicked: 0},
              {letter: 'b', asciicode: '98', isFav: false, clicked: 0},
              {letter: 'c', asciicode: '99', isFav: false, clicked: 0},
              {letter: 'd', asciicode: '100', isFav: false, clicked: 0},
              {letter: 'e', asciicode: '101', isFav: false, clicked: 0},
              {letter: 'f', asciicode: '102', isFav: false, clicked: 0},
              {letter: 'g', asciicode: '103', isFav: false, clicked: 0},
              {letter: 'h', asciicode: '104', isFav: false, clicked: 0},
              {letter: 'i', asciicode: '105', isFav: false, clicked: 0},
              {letter: 'j', asciicode: '106', isFav: false, clicked: 0},
              {letter: 'k', asciicode: '107', isFav: false, clicked: 0},
              {letter: 'l', asciicode: '108', isFav: false, clicked: 0},
              {letter: 'm', asciicode: '109', isFav: false, clicked: 0},
              {letter: 'n', asciicode: '110', isFav: false, clicked: 0},
              {letter: 'o', asciicode: '111', isFav: false, clicked: 0},
              {letter: 'p', asciicode: '112', isFav: false, clicked: 0},
              {letter: 'q', asciicode: '113', isFav: false, clicked: 0},
              {letter: 'r', asciicode: '114', isFav: false, clicked: 0},
              {letter: 's', asciicode: '115', isFav: false, clicked: 0},
              {letter: 't', asciicode: '116', isFav: false, clicked: 0},
              {letter: 'u', asciicode: '117', isFav: false, clicked: 0},
              {letter: 'v', asciicode: '118', isFav: false, clicked: 0},
              {letter: 'w', asciicode: '119', isFav: false, clicked: 0},
              {letter: 'x', asciicode: '120', isFav: false, clicked: 0},
              {letter: 'y', asciicode: '121', isFav: false, clicked: 0},
              {letter: 'z', asciicode: '122', isFav: false, clicked: 0},
              {letter: 'ü', asciicode: '129', isFav: false, clicked: 0},
              {letter: 'ä', asciicode: '132', isFav: false, clicked: 0},
              {letter: 'Ä', asciicode: '142', isFav: false, clicked: 0},
              {letter: 'ö', asciicode: '148', isFav: false, clicked: 0},
              {letter: 'Ö', asciicode: '153', isFav: false, clicked: 0},
              {letter: 'Ü', asciicode: '154', isFav: false, clicked: 0},
              {letter: 'ß', asciicode: '225', isFav: false, clicked: 0},


          ]
    }
  },
  computed: {
      favBooks(){
          return this.letters.filter((letter) => letter.isFav)
      },
      notFavBooks(){
          return this.letters.filter((letter) => !letter.isFav)
      },
      clickedLettersFilter(){
          return this.letters.filter((letter) => letter.clicked > 0)
      },
  }
}



</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  background-color: #262626;
  border: 2px solid black;
  border-radius: 10px;
  margin-left: 20px;
  margin-right: 20px;
}

img{
  margin-top: 20px;
  width: 80%;
  height: 80%;
}

button{
  color: white;
  margin-top: 20px;
  background-color: black;
  margin-bottom: 20px;
  border-radius: 10px;
}

h3{
   color: white;
}

.chartClass{
  background-color:#404040;
  width: 75%;
  border: 2px solid black;
  border-radius: 10px;
  margin: auto;
  margin-top: 20px; 
  display: auto;
  max-width: 75%;
  height: 400px;
  box-sizing: border-box;
}
</style>
