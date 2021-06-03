<template>
<div class ="keyboard"> 
    <LetterComponent v-for="letter in letters" v-bind:key="letter" :textValue="{letter}" v-on:onClickControlLetterToParent="onClickControlLetterToApp" v-on:onClickLetterToParent="onClickLetterToApp"></LetterComponent>
</div>
</template>

<script>
import LetterComponent from './LetterComponent.vue'
export default {
  components: {LetterComponent},
  data(){
      return{
          
      }
  },
  props: ['letters'],
  methods: {
      onClickControlLetterToApp(message){
          this.$emit("onClickControlLetterApp", message);
      },
      onClickLetterToApp(message){
          this.$emit("onClickLetterApp", message);
      }
  }
  
}
</script>


<style scoped>
.keyboard{
    background-color:#404040;
    width: 75%;
    border: 2px solid black;
    border-radius: 10px;
    margin: auto;
    margin-top: 20px;
    display: flex;
    flex-wrap: wrap;
    max-width: 75%;
    box-sizing: border-box;
}
</style>