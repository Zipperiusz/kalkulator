<template>
  <div id="window">
    <p id="title">Kalkulator</p>
    <div id="display">0</div>
    <div id="calcButtons">
      <div class="calcButton">CE</div>
      <div class="calcButton">C</div>
      <div class="calcButton"><img src="../assets/delete.png"></div>
      <div class="calcButton">÷</div>
      <div class="calcButtonN">7</div>
      <div class="calcButtonN">8</div>
      <div class="calcButtonN">9</div>
      <div class="calcButton">×</div>
      <div class="calcButtonN">4</div>
      <div class="calcButtonN">5</div>
      <div class="calcButtonN">6</div>
      <div class="calcButton">-</div>
      <div class="calcButtonN">1</div>
      <div class="calcButtonN">2</div>
      <div class="calcButtonN">3</div>
      <div class="calcButton">+</div>
      <div class="calcButton">±</div>
      <div class="calcButton">0</div>
      <div class="calcButton">,</div>
      <div class="calcButton">=</div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Calculator',
  props: {
    msg: String
  }

}
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
img
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
