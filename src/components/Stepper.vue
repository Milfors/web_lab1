
<template>
    <div>
      
 <v-stepper v-model="numStep">
     <v-stepper-header>
                <v-stepper-step :complete="numStep > 1"  step="F">
                    StepOne
                </v-stepper-step>
                 <v-divider></v-divider>
                <v-stepper-step :complete="numStep > 2" step="S">
                    StepTwo
                </v-stepper-step>
                 <v-divider></v-divider>
                <v-stepper-step :complete="numStep > 3" step="T">
                    StepThree
                </v-stepper-step>
    </v-stepper-header>
      <v-stepper-items>

        <v-stepper-content step="1">  
     <form>
         <div class="container">

        <h1>Log in to the electronic journal</h1>
        <hr>
          <label for="Your name"><h2>Name</h2></label>
          <input v-model="name" type="text" placeholder="Full name" name="name" required>
          <label for="Student ID number"><h2>Student ID number</h2></label>
          <input v-model ="id" type="text" placeholder="st000000" name="Id" required>
          
          <p>{{Error}}</p>
          <div class="button" @click="click_button_Loggin">Next</div>
         </div>
    </form>
        </v-stepper-content>
            <v-stepper-content step="2">
     <form>
        <div class="container">
        <h1>Сonfirmation</h1>
        <p>Сonfirm your account by entering your email</p>
        <hr>

    <label for="Your email"><b>Enter your email</b></label>
    <input v-model="email" type="email" placeholder= "ema@i.l" name="email" required>
    <p>{{Error}}</p>
    <div class="button" @click="click_button2">Next</div>
  </div>
</form>        
 </v-stepper-content>
            <v-stepper-content step="3">
      <form>
        <div class="container">
        <h1>Добро пожаловать!</h1>
        <h3>Вы зашли в свой аккаунт</h3>
        <hr>
            
            
            
            <div class="button" @click="click_reset">Resert</div>
  </div>
</form>
            </v-stepper-content>
        </v-stepper-items>
        </v-stepper>
  </div>

  
   
</template>


<script >
document.body.style.backgroundColor = "#AA0000";

export default {
    name: 'Stepper1',

    data: function(){
    return { 
      //  currentTab:0,
        name:"",
        id:"",
        email:"",
        Error:"",
        numStep: 1
    }
      
    },
    methods:{
click_button_Loggin: function() {

    if(this.name=="")
      this.Error = "Error: Enter correct your name"
     if(this.id=="")
     this.Error = "Error: Enter correct your id"
     if(this.id!="" && this.name!="")
     {
        this.numStep = this.numStep+1
        this.Error=""
     }
},
click_button2: function() {

   if(this.email=="")
      this.Error = "Enter email"    
  else
    {
      this.numStep = this.numStep+1
      this.Error=""
    }
},
click_reset : function() {
    this.numStep=1
    this.email=""
    this.name=""
    this.id=""
}, 
click_button_ID: function() {
    
    this.Error = "Invalid id entered"
},
}
}
</script>
<style scoped>

* {box-sizing: border-box}

/* Add padding to containers */
.container {
  padding: 18px;
}

/* Full-width input fields */
input[type=text], input[type=email] {
  width: 50%;
  padding: 20px;
  margin: 5px 0 10px 0;
  display: inline-block;
  border: none;
  border-radius: 10px;
  background: #382a38;
   
}

input[type=text]:focus, input[type=email]:focus {
  background-color: rgb(65, 53, 68);
  border-radius: 10px;
  outline: none;
}

/* Overwrite default styles of hr */
hr {
  border: 2px dotted #3a2a39d8;
  margin-bottom: 2px;
}

/* Set a style for the submit/register button */
.button {
  background-color: #8100d6;
  color: rgb(8, 8, 8);
  padding: 16px 20px;
  margin: 8px 2;
  border: none;
  cursor: pointer;
  align-content: center;
  width: 100px;
  border-radius: 10px;
  opacity: 0.9;
  position: relative;
  left: 50%;
  transform: translate(-50%, 0);
}

.registerbtn:hover {
  opacity:1;
}

/* Set a grey background color and center the text of the "sign in" section */
.signin {
  background-color: #e896f8;
  text-align: center;
}

</style>