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
    <Chart> </Chart>
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
    },
    onClickControlLetter(message){
      message.letter.isFav = !message.letter.isFav;
    },
    onClickLetter(message){
      console.log(message);
      message.letter.clicked++;
      console.log(message);
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
              {letter: 'a', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'b', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'c', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'd', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'e', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'f', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'g', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'h', asciicode: '90', isFav: false, clicked: 0},
              {letter: 'i', asciicode: '90', isFav: false, clicked: 0},


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
  height: 300px;
  box-sizing: border-box;
}
</style>
