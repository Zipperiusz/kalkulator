<template>
  <div id="window">
    <p id="title">Kalkulator</p>
    <div id="log">{{ operationLog }}</div>
    <div id="display">{{ displayed }}</div>
    <div id="calcButtons">
      <div @click="percent()" class="calcButton">%</div>
      <div @click="clearAll()" class="calcButton">C</div>
      <div @click="deleteNumber()" class="calcButton">
        <img id="delete" src="../assets/delete.png" />
      </div>
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
export default {
  name: "calculator",
  data() {
    return {
      displayed: "",
      numbers: []
    };
  },
  beforeMount() {
    window.addEventListener("keyup", this.onKeyUp);
  },
  beforeDestroy() {
    window.removeEventListener("keyup", this.onKeyUp);
  },
  methods: {
    onKeyUp(e)
    {
      if (/^\d$/.test(e.key))
      {
        this.displayNumber(+e.key);
      }
    },
    displayNumber(number)
    {
      if (this.displayed.length <= 16)
      {
        this.displayed = this.displayed + number;
        if(this.displayed.length==2)
        {
          if(this.displayed[0,1]==0)
          this.displayed= "0";
          if(this.displayed[0]==0)
          {
            this.displayed = number.toString();
          }
        }
      }
    },
    addAction(e)
    {
      this.isDoubleMinus();
      if (this.displayed.length)
      {
        this.numbers.push(this.displayed);        
      }
      if (this.isAction())
      {
        this.$set(this.numbers, this.numbers.length - 1, e);
      }
      else if(this.displayed.length)
      {
        this.numbers.push(e);
      }
      this.displayed = "";
      
    },
    deleteNumber()
    {
      this.displayed = this.displayed.slice(0, -1);
    },
    clearAll()
    {
      this.displayed = "";
      this.numbers = [];
    },
    invert()
    {
      if (this.displayed.length)
      {
        if (this.displayed[0] == "-")
        {
          this.displayed = this.displayed.substring(1);
        } 
        else
        {
          this.displayed = "-" + this.displayed;
        }
      }
    },
    isAction()
    {
      if (this.numbers.length >= 2)
      {
        const sign = this.numbers[this.numbers.length - 1];
        if (sign === "*" || sign === "-" || sign === "+" || sign === "/")
        {
          return true;
        }
        return false;
      }
      return false;
    },
    addComma()
    {
      if(this.displayed.length)
      {
        if(!this.displayed.includes("."))
        {
          this.displayed = this.displayed + ".";
        }
      }
    },
    percent()
    {
      if(this.displayed.length)
      {
      this.displayed = this.displayed * 0.01;
      this.displayed = this.displayed.toString();
      }     

    },
    isDoubleMinus()
     {
       if(this.numbers[this.numbers.length-1]=="-")
       {
       if(this.displayed<0)
       {        
        this.displayed = this.displayed.substring(1);
        this.numbers[this.numbers.length-1]="+";       
       }
         
       }        
     },
    getResult()
    {
      if (this.isAction())
      {
        if(this.displayed.length==0)
        {
          this.numbers.pop();
          
        }
        else
        {
          this.isDoubleMinus();
          this.numbers.push(this.displayed);
        }
        
        this.displayed = eval(this.numbers.join("")).toString();
        this.numbers = [];        
      }
    }
  },
  computed: {
    operationLog() {
      return this.numbers.join("");
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#window {
  background-color: #3f4041;
  width: 400px;
  height: 400px;
  margin-left: auto;
  margin-right: auto;
  color: white;
}
#display {
  text-align: right;
  padding: 8px;
  font-size: 24px;
  width: 356px;
  margin-left: auto;
  margin-right: auto;
  height: 20px;
  letter-spacing: 1px;
}
#log {
  text-align: right;
  padding: 8px;
  font-size: 10px;
  width: 356px;
  margin-left: auto;
  margin-right: auto;
  height: 20px;
  letter-spacing: 1px;
}
.calcButtonN {
  text-align: center;
  display: inline-block;
  padding: 15px;
  width: 60px;
  background-color: #242525;
  margin: 2px;
  cursor: pointer;
}
#delete {
  width: 14px;
}
.calcButtonN:hover {
  background-color: #717274;
}
.calcButton {
  text-align: center;
  display: inline-block;
  padding: 15px;
  width: 60px;
  background-color: #333535;
  margin: 2px;
  cursor: pointer;
}
.calcButton:hover {
  background-color: #717274;
}
#title {
  text-align: left;
  padding: 10px;
  color: #7f8585;
}
</style>
