<template>
  <div id="window" >
    <GlobalEvents @keyup.48.96="displayNumber(0)" @keyup.49.97="displayNumber(1)" @keyup.50.98="displayNumber(2)" @keyup.51.99="displayNumber(3)" @keyup.52.100="displayNumber(4)" @keyup.53.101="displayNumber(5)" @keyup.54.102="displayNumber(6)" @keyup.55.103="displayNumber(7)" @keyup.56.104="displayNumber(8)" @keyup.57.105="displayNumber(9)" @keyup.187="addAction('+')" @keyup.189="addAction('-')" @keyup.*="addAction('*')" @keyup.191="addAction('/')" />
    <p id="title">Kalkulator</p>
    <div id="log">{{ Numbers }}</div>
    <div id="display">{{ displayed }}</div>
    <div id="calcButtons">
      <div class="calcButton">%</div>
      <div @click="clearAll()" class="calcButton">C</div>
      <div @click="deleteNumber()" class="calcButton"><img id="delete" src="../assets/delete.png"></div>
      <div @click="addAction('/')" class="calcButton">÷</div>
      <div @click="displayNumber(7)" class="calcButtonN">7</div>
      <div @click="displayNumber(8)" class="calcButtonN">8</div>
      <div @click="displayNumber(9)" class="calcButtonN">9</div>
      <div @click="addAction('*')" class="calcButton">×</div>
      <div @click="displayNumber(4)" class="calcButtonN">4</div>
      <div @click="displayNumber(5)" class="calcButtonN">5</div>
      <div @click="displayNumber(6)" class="calcButtonN">6</div>
      <div @click="addAction('-')" class="calcButton">-</div>
      <div @click="displayNumber(1)" class="calcButtonN">1</div>
      <div @click="displayNumber(2)" class="calcButtonN">2</div>
      <div @click="displayNumber(3)" class="calcButtonN">3</div>
      <div @click="addAction('+')" class="calcButton">+</div>
      <div @click="invert()" class="calcButton">±</div>
      <div @click="displayNumber(0)" class="calcButtonN">0</div>
      <div @click="addComma()" class="calcButton">,</div>
      <div @click="getResult()" class="calcButton">=</div>
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
      displayed:"",
      Numbers:"",
      result:undefined

      
    }
  },
  methods:
  {
    displayNumber(number){
      if(this.displayed.length<=16)
      {      
      this.displayed = this.displayed+number;
      }

    },
    addAction(e){
      if(this.displayed!==""){
      if(!this.checkSign()){
      this.Numbers =this.Numbers +  this.displayed+e;
      this.displayed="";
      }
      }

    },
    deleteNumber()
    {
      this.displayed = this.displayed.toString();
      this.displayed = this.displayed.slice(0, -1);
    },
    clearAll()
    {
      this.displayed = "";
      this.Numbers = "";
      this.result = undefined;
    },
    invert()
    {
      this.displayed = Number(this.displayed);
      if(this.displayed!==undefined);
      {

        this.displayed = this.displayed*-1;
        this.displayed = this.displayed.toString();
      }
    },
    checkSign(){
      if(this.Numbers.charAt(this.Numbers.length-1)=== "*"||"-"||"+"||"/")
      {
        return false;
      }
      else return true;
    },
    checkComma(){
      if(this.displayed.charAt(this.displayed.length-1)=== ",")
      {
        return false;
      }
      else return true;
    },
    getResult()
    {
     
     this.displayed = eval(this.Numbers+this.displayed);
     this.Numbers="";
     
    },
    addComma(){
      if(checkSign)
      this.displayed += ",";
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
  height: 400px;
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
#log
{
  text-align: right;
  padding:8px;
  font-size:10px;
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
