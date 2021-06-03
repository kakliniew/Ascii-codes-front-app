<template>
  <img alt="ascii codes logo" src="./assets/logo.png">
  <h3 v-if="showKeys">Favourite letters</h3>
  <KeysBoard v-if="showKeys" :letters="favBooks" @onClickControlLetterApp="onClickControlLetter" @onClickLetterApp="onClickLetter"></KeysBoard>
  <h3 v-if="showKeys">All letters</h3>
  <KeysBoard v-if="showKeys" :letters="notFavBooks" @onClickControlLetterApp="onClickControlLetter" @onClickLetterApp="onClickLetter"></KeysBoard>
  <TextBox :textValue="textboxText"></TextBox>
  <button @click="ButtonOnClick" id="showButtons">{{buttonCaption}}</button>
</template>

<script>

import TextBox from './components/TextBox.vue'
import KeysBoard from './components/KeysBoard.vue'
export default {
  name: 'App',
  components: {KeysBoard, TextBox},
  methods: {
    ButtonOnClick(){
      this.showKeys = !this.showKeys;
      if (this.showKeys){
        this.buttonCaption = "Hide button keys"
      }else{
        this.buttonCaption = "Show button keys"
      }  
    },
    onClickControlLetter(message){
      message.letter.isFav = !message.letter.isFav;
    },
    onClickLetter(message){
      console.log(message);
      this.textboxText = this.textboxText + message.letter.letter;
    }
  },
  data(){
    return {
      showKeys: true,
      textboxText: '',
      buttonCaption: "Hide button keys",
      letters: [
              {letter: 'A', asciicode: '65', isFav: false},
              {letter: 'B', asciicode: '66', isFav: false},
              {letter: 'C', asciicode: '67', isFav: false},
              {letter: 'D', asciicode: '68', isFav: false},
              {letter: 'E', asciicode: '69', isFav: false},
              {letter: 'F', asciicode: '70', isFav: false},
              {letter: 'G', asciicode: '71', isFav: false},
              {letter: 'H', asciicode: '72', isFav: false},
              {letter: 'I', asciicode: '73', isFav: false},
              {letter: 'J', asciicode: '74', isFav: false},
              {letter: 'K', asciicode: '75', isFav: false},
              {letter: 'L', asciicode: '76', isFav: false},
              {letter: 'M', asciicode: '77', isFav: false},
              {letter: 'N', asciicode: '78', isFav: false},
              {letter: 'O', asciicode: '79', isFav: false},
              {letter: 'P', asciicode: '80', isFav: false},
              {letter: 'Q', asciicode: '81', isFav: false},
              {letter: 'R', asciicode: '82', isFav: false},
              {letter: 'S', asciicode: '83', isFav: false},
              {letter: 'T', asciicode: '84', isFav: false},
              {letter: 'U', asciicode: '85', isFav: false},
              {letter: 'V', asciicode: '86', isFav: false},
              {letter: 'W', asciicode: '87', isFav: false},
              {letter: 'X', asciicode: '88', isFav: false},
              {letter: 'Y', asciicode: '89', isFav: false},
              {letter: 'Z', asciicode: '90', isFav: false},
              {letter: 'a', asciicode: '90', isFav: false},
              {letter: 'b', asciicode: '90', isFav: false},
              {letter: 'c', asciicode: '90', isFav: false},
              {letter: 'd', asciicode: '90', isFav: false},
              {letter: 'e', asciicode: '90', isFav: false},
              {letter: 'f', asciicode: '90', isFav: false},
              {letter: 'g', asciicode: '90', isFav: false},
              {letter: 'h', asciicode: '90', isFav: false},
              {letter: 'i', asciicode: '90', isFav: false},


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
</style>
