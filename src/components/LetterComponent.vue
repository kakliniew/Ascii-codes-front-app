<template>
    <div :class ="letterClass" @click.ctrl="onClickControlLetter(textValue)" @click.alt="onLetterClickAlt" @click.exact="onLetterClick(textValue)">
        <label>{{labelValue}}</label>
    </div>
</template>


<script>

export default {
    props: ['textValue'],
  data(){
      return{
          letterClicked: false
      }
  },
  methods: {
      onClickControlLetter(letter){
        this.$emit("onClickControlLetterToParent", letter);
      },
      onLetterClickAlt(){
          this.letterClicked = !this.letterClicked;
      },
      onLetterClick(letter){
        this.$emit("onClickLetterToParent", letter);
      }
  },
  computed: {
      letterClass(){
          return this.textValue.letter.isFav ? 'letterClass textColor' :'letterClass' ;
      },
      labelValue(){
          if (this.letterClicked){
              return  this.textValue.letter.asciicode;
          }
          else{
             return this.textValue.letter.letter;
          }
      }
  }

}
</script>


<style>
.letterClass{
    background-color: #595959;
    width: 40px;
    height: 40px;
    border: 2px solid black;
    border-radius: 10px;
    text-align: center;
    color:coral;
    margin: 2px;
  
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0 8px 6px -6px black;
    box-sizing: border-box;
}
.textColor{
    color:hotpink;
}

label{
    text-shadow: 2px 2px black;
}
</style>