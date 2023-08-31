<script lang="ts">
export default {
name : "App",
data() {
  return {
    user_name : "Joe",
    idOfDiv : "thisIsDivID",
    isButtonDisabled : true,
    form : "<span><i>This is a dynamic HTML</i></span>",
    validInput : true,
    arrayCondition1 : false,
    arrayCondition2 : true,
    display : true,
    age : 18,
    names : ["Aman","Krishna","Chinmay"],
    ageGroup : [{
      name: "Ram",age : 22},
     { name : "Sham",age : 26, },
      {name: "Golu",age:24},
    ],
    flexStyles : {
      display : "flex", 
      "justify-content" :"center",
      "align-items" : "center",
    },
    flexColumn :  {
      display : "flex", 
      "justify-content" :"center",
      "align-items" : "center",
      "flex-direction" : "column"
    },
    numbersArray : [123,34,234,234524,5424334,34]
  }
},
  methods: {
    add(num:number){
      return num < this.age 
    },
    handleForm(event : any){
      event.preventDefault();
    },

  },
  computed : {
    calculateSum(){
      return this.numbersArray.reduce((total:number, num:number) => total+num)
    }
  }
}
</script>

<template >
  <h1>{{ user_name }}</h1>
  <h1 v-html="form"></h1>
  <div :id="idOfDiv"></div>
  <button :disabled="isButtonDisabled">disabled</button>
  <p :class="isButtonDisabled && 'valid'"> & condition</p>
  <p :class="validInput ?'valid' : 'inValid'"> ternary condition</p>
  <p :class="[arrayCondition1 && arrayCondition2 ? 'valid' : 'inValid']"> array class binding</p>
  <p :class="{
    valid : validInput,
    invalid : !validInput,
    none : arrayCondition1
  }">Object Class binding</p>
  <input 
    v-bind:class="validInput ? 'valid' : 'inValid'"
    type="text" 
    id="user_name"
  v-model="user_name"     
  />

  <!-- conditional rendering -->

  <h5 v-if="validInput">If input is valid then only this line will be rendered</h5>

  <!-- Multiple conditions -->
  <template v-if="display">
    <p v-if="age === 18">If age is equal 18</p>
    <p v-else-if="age > 18">If age is greater then 18</p>
    <p v-else-if="age < 18">If age is less then 18</p>
    <p v-else>No age limit</p>
  </template>

  <!-- For loop  -->

  <h1 v-for="name in names" :key="name">{{ name }}</h1>
  <h1 v-for="(name, index) in names" :key="name">{{index+1}} {{ name }}</h1>
  <span v-for="(person,index) in ageGroup" :key="index">{{person.name}}{{ person.age }}</span>
  <span v-for="(value,key,index) in flexStyles" :key="index">{{ index }} {{ key }} : {{ value }}</span>

  <!-- Methods -->

  <h1>Methods{{ add(12) }}</h1>
  <!-- Event Handling -->
  <button v-on:click="validInput = !validInput">Click me</button>

  <!-- Modifiers -->
  <form v-on:submit.prevent="handleForm">
    <input type="text" name="name" placeholder="Enter your name" v-model.trim.lazy="user_name"     />
    <input @keyup.enter="handleForm" type="submit" value="Submit">
  </form>

  <h1> {{ calculateSum }}</h1>
</template>
 <!-- Calculating sum of all elements in an array -->

<style scoped>
.valid{
  border: 2px solid lime;
  color : green;
  margin-top: 15px;
  gap: 15px;
  margin-left: 10px;
  font-family: "Poppins",serif;
}
.inValid{
  border: 2px solid red;
  margin-top: 15px;
  gap: 15px;
  font-family: "Poppins",serif;
}
.none{
  display: none;
}
</style>
