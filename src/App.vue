<template>
  <div>
    <h1>My name is {{ name.toUpperCase() }} and {{ age }} year{{age>1 ? "s":""}} old
    {{pronoun}} was born in {{birthYear}}</h1>
  </div>
  <input type="text" v-model="inputName">
  <button v-on:click="changeName">Click</button>

  <div class="my-4">
    <h1 v-if="age>=18">
      {{name}} can vote
    </h1>
    <h1 v-else>
      {{name}} can't vote
    </h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name : " kabyar",
      age : 8,
      gender : "female",
      inputName : ""
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
    }
  },
}
</script>

<style scoped>

</style>