<template>
    <div :class ="letterClass" @click.ctrl="onClickControlLetter(textValue)" @click.alt="onLetterClickAlt" @click.exact="onLetterClick(textValue)">
        <label>{{labelValue}}</label>
        <div class="angle-shadow left-top top-section"></div>
        <div class="angle-shadow right-top top-section"></div>
        <div class="angle-shadow left-bottom bottom-section"></div>
        <div class="angle-shadow right-bottom bottom-section"></div>
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
    position: relative;
  z-index: 50;

  display: flex;
  justify-content: center;
  width: 40px;
  height: 40px;
  overflow: hidden;

  background-color: #b7ad9b;
  border: 2px solid #857e71;
  border-radius: 6px;
  cursor: pointer;

  transition: 0.1s;
}
.textColor{
    color:hotpink;
}

label{
   position: relative;
  top: 4px;
  z-index: 100;

  display: flex;
  justify-content: center;
  align-items: center;
  width: 24px;
  height: 24px;

  font-size: 20px;
  font-family: Arial, Helvetica, sans-serif;
  color: black;

  background-color: #eee0ce;
  border: 2px solid #f6e5d6;
  border-radius: 6px;
  box-shadow: 
    0 -20px 20px 6px #f6e5d6,
    inset 0px -1.6px 4px #baaf9e;

  transition: 0.1s;

  -webkit-user-select:      none;
     -moz-user-select: -moz-none;
          user-select:      none;

   -khtml-user-select:      none;
       -o-user-select:      none;
}

.letterClass::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  z-index: 50;

  width: 90%;
  height: 90%;

  border: 2px solid #d9ccbc;
  border-radius: 4px;
}

.letterClass:active {
  box-shadow: inset 0 -20px 14px #857e71;
}

.letterClass:active label {
  width: 22px;
  height: 22px;

  font-size: 18px;
}

.letterClass:active label {
  width: 22px;
  height: 22px;

  font-size: 18px;

  box-shadow: 0 -20px 20px 6px #f6e5d6,
  inset 0px 2px 4px #baaf9e;
}

.angle-shadow {
  position: absolute;
}

.angle-shadow.top-section {
  top: 6px;

  width: 14px;
  height: 1px;

  background-color: #f6e5d6;
  box-shadow: 0 0 2px #f6e5d6;
}

.angle-shadow.bottom-section {
  bottom: 0px;

  border-right: 2px solid transparent;
  border-bottom: 18px solid #dfd2bf;
  border-left: 2px solid transparent;
}

.angle-shadow.left-top {
  left: 1px;
  transform: rotate(36deg);
}

.angle-shadow.right-top {
  right: 1px;
  transform: rotate(-36deg);
}

.angle-shadow.left-bottom {
  left: 5px;
  transform: rotate(30deg);
}

.angle-shadow.right-bottom {
  right: 5px;
  transform: rotate(-30deg);
}
</style>