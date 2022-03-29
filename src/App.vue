<template>
  <div>
    <h1>My name is {{ name.toUpperCase() }} and {{ age }} year{{age>1 ? "s":""}} old
    {{pronoun}} was born in {{birthYear}}</h1>
  </div>
  <input  type="text" v-model="inputName">
  <button class="btn btn-primary" v-on:click="changeName">Click</button>

  <div class="my-4">
    <h1 v-if="age>=18">
      {{name}} can vote
    </h1>
    <h1 v-else>
      {{name}} can't vote
    </h1>
  </div>

  <div class="my-3">
    <div class="row g-2">
      <div class="col-6">
        <input type="text" class="form-control" v-model="inputFruit" @keyup.enter="addFruit">
      </div>
      <div class="col-4">
        <button class="btn btn-primary"  @click="addFruit">Add</button>
      </div>
      <ul class="list-group">
        <li class="list-group-item" v-for="(fruit,index) in fruits" v-bind:key="index">{{ fruit }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name : " kabyar",
      age : 8,
      gender : "female",
      inputName : "",
      fruits : ["mango","orange","apple"],
      inputFruit:'',

    }
  },
  computed: {
    pronoun(){
      return this.gender === "male" ? "He":"she";
    },
    birthYear(){
      return new Date().getFullYear() - this.age;
    }
  },
  methods: {
    showAlert(){
      alert("hello");
    },
    changeName(){
      this.name = this.inputName
      this.inputName = null
    },
    addFruit(){

      //တခုခုထဲ့ပီးenterမှထဲ့မယ် plain ဆိုမရ
      if (!this.inputFruit){
        console.log("plain")
        return;
      }

      //အပေါ်ကနေထည့်တာ
      this.fruits=[this.inputFruit,...this.fruits]
      // this.fruits.unshift(this.inputFruit)

      //အောက်ကနေထည့်တာ
      // this.fruits=[...this.fruits,this.inputFruit]
      // this.fruits.push(this.inputFruit)
      this.inputFruit=null
    }
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Hurricane&display=swap');
$primary: violet;
$font-family-sans-serif:'Hurricane', cursive;
  @import "~bootstrap/scss/bootstrap";
</style>