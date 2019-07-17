<template>
  <div id="window" >
    <GlobalEvents @keyup.48.96="addNumber(0)" @keyup.49.97="addNumber(1)" @keyup.50.98="addNumber(2)" @keyup.51.99="addNumber(3)" @keyup.52.100="addNumber(4)" @keyup.53.101="addNumber(5)" @keyup.54.102="addNumber(6)" @keyup.55.103="addNumber(7)" @keyup.56.104="addNumber(8)" @keyup.57.105="addNumber(9)" />
    <p id="title">Kalkulator</p>
    <div id="display">{{ displayed }}</div>
    <div id="calcButtons">
      <div class="calcButton">CE</div>
      <div class="calcButton">C</div>
      <div class="calcButton"><img id="delete" src="../assets/delete.png"></div>
      <div class="calcButton">÷</div>
      <div @click="addNumber(7)" class="calcButtonN">7</div>
      <div @click="addNumber(8)" class="calcButtonN">8</div>
      <div @click="addNumber(9)" class="calcButtonN">9</div>
      <div class="calcButton">×</div>
      <div @click="addNumber(4)" class="calcButtonN">4</div>
      <div @click="addNumber(5)" class="calcButtonN">5</div>
      <div @click="addNumber(6)" class="calcButtonN">6</div>
      <div class="calcButton">-</div>
      <div @click="addNumber(1)" class="calcButtonN">1</div>
      <div @click="addNumber(2)" class="calcButtonN">2</div>
      <div @click="addNumber(3)" class="calcButtonN">3</div>
      <div class="calcButton">+</div>
      <div class="calcButton">±</div>
      <div @click="addNumber(0)" class="calcButton">0</div>
      <div class="calcButton">,</div>
      <div @click="convert()" class="calcButton">=</div>
    </div>

  </div>
</template>

<script>
import GlobalEvents from 'vue-global-events'
export default {
  components: { GlobalEvents },
  name: 'calculator',
  data(){
    return{
      displayed:""
    }
  },
  methods:
  {
    addNumber(number){
      if(this.displayed.length<=16)
      {
      this.displayed = this.displayed+number;
      }
      else
      {
        this.displayed = this.displayed;
      }

    },
    convert(){
      this.displayed = Number(this.displayed);
      //Test konwersji stringa na liczbę
    }    
  }
}

//pobieranie wartości wciśniętego przycisku
//window.addEventListener('keydown', function(e) {
//  console.log(e.key);
//});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#window
{
  background-color:#3f4041;
  width:400px;
  height: 365px;
  margin-left: auto;
  margin-right:auto;
  color:white;
}
#display
{
  text-align: right;
  padding:8px;
  font-size:24px;
  width:356px;
  margin-left:auto;
  margin-right:auto;
  height:20px;
  letter-spacing: 1px;
}
.calcButtonN
{
  text-align: center;
  display:inline-block;
  padding:15px;
  width:60px;
  background-color:#242525;
  margin:2px;
  cursor: pointer;
  
}
#delete
{
  width:14px;
}
.calcButtonN:hover
{
  background-color:#717274;
}
.calcButton
{
  text-align: center;
  display:inline-block;
  padding:15px;
  width:60px;
  background-color:#333535;
  margin:2px;
  cursor: pointer;
  
}
.calcButton:hover
{
  background-color:#717274;
}
#title
{
  text-align:left;
  padding:10px;
  color:#7f8585;
}
</style>
