<template>
  <div id="window">
    <p id="title">Kalkulator</p>
    <div id="display">d</div>
    <div id="calcButtons">
      <div class="calcButton">7</div>
      <div class="calcButton">8</div>
      <div class="calcButton">9</div>
      <div class="calcButton">4</div>
      <div class="calcButton">5</div>
      <div class="calcButton">6</div>
      <div class="calcButton">1</div>
      <div class="calcButton">2</div>
      <div class="calcButton">3</div>
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
  width:350px;
  margin-left: auto;
  margin-right:auto;
  color:white;
}
#display
{
  text-align: right;
  padding:8px;
  font-size:24px;
}
.calcButton
{
  text-align: center;
  display:inline-block;
  width:100px;
  height: 60px;
  background-color:#242525;
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
