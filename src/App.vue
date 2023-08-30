<script lang="ts">
export default {
name : "App",
data() {
  return {
    name : "Joe",
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
    }
  }
}
}
</script>

<template >
  <h1>{{ name }}</h1>
  <h1 v-html="form"></h1>
  <div v-bind:id="idOfDiv"></div>
  <button v-bind:disabled="isButtonDisabled">disabled</button>
  <p v-bind:class="isButtonDisabled && 'valid'"> & condition</p>
  <p v-bind:class="validInput ?'valid' : 'inValid'"> ternary condition</p>
  <p v-bind:class="[arrayCondition1 && arrayCondition2 ? 'valid' : 'inValid']"> array class binding</p>
  <p v-bind:class="{
    valid : validInput,
    invalid : !validInput,
    none : arrayCondition1
  }">Object Class binding</p>
  <input v-bind:class="validInput ? 'valid' : 'inValid'" type="text" name="name input" placeholder="Enter your name">

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
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500&display=swap');
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
