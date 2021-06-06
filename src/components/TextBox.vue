<template>
    <div class ="textbox">
        <span>{{textValue}}</span>
    </div>
</template>


<script>

export default {
  data(){
      return{
         
      }
  },
  props: ['textValue']
  
}
</script>


<style>
.textbox{
    background-color:#404040;
    width: 75%;
    height: 150px;
    border: 2px solid black;
    border-radius: 10px;
    margin: auto;
    margin-top: 20px;
    color: white;
    font-size: large;
    display: flex;
    flex-wrap: wrap;
    overflow-wrap: break-word;
    word-wrap: break-word;

}

.textbox span{
    overflow-wrap: break-word;
    word-wrap: break-word;
    box-sizing: border-box;
    max-width: 100%;
}
</style>