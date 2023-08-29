<script lang="ts">
export default {
name : "App",
data() {
  return {
    name : "Joe",
    idOfDiv : "thisIsDivID",
    isButtonDisabled : true,
    form : "<span><i>This is a dynamic HTML</i></span>",
    validInput : true
  }
}
}
</script>

<template>
  <h1>{{ name }}</h1>
  <h1 v-html="form"></h1>
  <div v-bind:id="idOfDiv"></div>
  <button v-bind:disabled="isButtonDisabled">disabled</button>
  <p v-bind:class="validInput && 'valid'"> & condition</p>
  <p v-bind:class="validInput && 'valid'"> ternary condition</p>
  <p v-bind:class="validInput && 'valid'"> array condition</p>
  <input v-bind:class="validInput ? 'valid' : 'inValid'" type="text" name="name input" placeholder="Enter your name">
</template>

<style scoped>
.valid{
  border: 2px solid lime;
  color : green;
}
.inValid{
  border: 2px solid red;
}
</style>
