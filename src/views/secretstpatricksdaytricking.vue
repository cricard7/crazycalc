<template>
  <div class="about">
    <div class="containter-fluid">
    <h1>Hope you like this calulator. It's the best in the world!</h1>


    <div class="row">

      <div class="col-md-6 offset-md-3">

  <div class="card">
  
  <div class="card-body">
    

    <div class="row mb-2">
      <div class="col-md-12">
          <div class="card">
          <div class="card-body">
            <h1 class="display-1"><span>{{opOne}}</span><span v-html="operator"></span><span>{{opTwo}}</span><span>{{answer}}</span></h1>
          </div>
        </div>
      </div>
    </div>

    <div class="row">
            <div class="col-md-4">
              <button @click="pressed(4)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">7</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed(5)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">8</button>
            </div> <div class="col-md-4">
              <button @click="pressed(6)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">9</button>
            </div> <div class="col-md-4">
              <button @click="pressed(7)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">4</button>
            </div> <div class="col-md-4">
              <button @click="pressed(8)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">5</button>
            </div> <div class="col-md-4">
              <button @click="pressed(9)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">6</button>
            </div> <div class="col-md-4">
              <button @click="pressed(0)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">1</button>
            </div> <div class="col-md-4">
              <button @click="pressed('=')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">2</button>
            </div> <div class="col-md-4">
              <button @click="pressed('OFF')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">3</button>
            </div> <div class="col-md-4">
              <button @click="pressed(1)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">0</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed(2)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">=</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed(3)" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">off</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed('/')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">+</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed('AC')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">-</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed('X')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">X</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed('+')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">&#247;</button>
            </div>
            <div class="col-md-4">
              <button @click="pressed('-')" type="button" class="btn btn-secondary disbled btn-lg btn-block mb-2">AC</button>
            </div>

          <!--
            7 -> 4
            8 -> 5
            9 -> 6
            1 -> 0
            2 -> =
            3 -> off
            + -> divide
            - -> AC
            X - > X
           -->

      </div> 

      </div> 
      
     
      
    </div>

   

  </div>
</div>

      </div>

    </div>

    


  
</template>

<script>
// @ is an alias to /src

export default {
  name: 'calc',
  components: {
    
  },
  data: function(){
    return {
      on: false,
      printed: "",
      opOne: "",
      opTwo: "",
      operator: "",
      loc: "first", //  'first' ,'second'  operand being entered
      answer: ""
    }

  },

  methods: {

    pressed: function(val){


       // hit equal
       if (val === '='){
        
         // make sure there are values in opOne and opTwo
            if(this.opOne !== '' && this.opTwo !== ''){
                
                if(this.operator === '+'){
                  this.answer = eval(Number(this.opOne) + Number(this.opTwo))
                } 
                 if(this.operator === '-'){
                  this.answer = eval(Number(this.opOne) - Number(this.opTwo))
                }
                 if(this.operator === 'X'){
                  this.answer = eval(Number(this.opOne) * Number(this.opTwo))
                }
                 if(this.operator === '&#247;'){
                  this.answer = eval(Number(this.opOne) / Number(this.opTwo))
                }

                this.opOne = ""
                this.opTwo = ""
                this.operator = ""

            }
         

        return
       }

       // hit off or AC 

      if (val === 'OFF' || val === 'AC'){
        this.opOne = ""
        this.opTwo = ""
        this.operator = ""
        this.answer = ""
        return
      }

      // if an operator key is hit

       // hit plus

      if (val === '+'){
        
        this.operator = "+"
        
        return

      }

      // hit minus
      if (val === '-'){
        this.operator = "-"
        
        return

      }

      // hit divide
      if(val === '/'){
        this.operator = "&#247;"
        
        return

      }

      //hit times
      if(val === 'X'){
        this.operator = "X"
        
        return
      }
      
      // fill opOne if no operator
      if(this.operator === ''){
        this.opOne = String(this.opOne) + String(val)
        this.answer = ''
      }

      // else fill opTwo
      else if(this.operator !== ''){
        this.opTwo = String(this.opTwo) + String(val)
        this.answer = ''
      }

     

    /*

      //hit times (x)

      if (val === 'X'){
              this.opOne = this.printed
              this.operator = "X"
              this.printed = String(this.printed) + String(val)
              return

            }
      // hit divide (+)
         if (val === '&#247;'){
              this.opOne = this.printed
              this.operator = "&#247;"
              this.printed = String(this.printed) + String(val)
              return

            }
      // hit on (-)

         if (val === 'ON'){
              this.on = true
              this.printed = " "
              return
          }

      */
      

    }

  },

  watch: {
    

  }
}
</script>