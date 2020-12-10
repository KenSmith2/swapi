<template>
<div id="example-2">
  App Started
  <hr>
  <button v-on:click="getData(1)">1</button>
  <button v-on:click="getData(2)">2</button>
  <button v-on:click="getData(3)">3</button>
  <hr>
  <form>
  <select v-model="value" v-on:click="getData(value)" class="form-control">
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
  </select>
  </form>

  <form v-on:submit.prevent v-on:click="getData(value)">
    <input type="text" v-model="value">
    
    <button>Enter</button>
  </form>
  <div>{{ fullName }}</div>
  <div>{{ fullHeight }}</div>
</div>
</template>


<script>
import axios from 'axios'
let fullName = ''
let fullHeight = ''

export default {


 methods: {
      getData (value) {
            axios
              .get(`https://swapi.dev/api/people/${value}/`)
              .then((result) => {
                this.fullName = result.data.name
                this.fullHeight = result.data.height
              })
      }
    },

  data() {
//let fullName = 'Name Here'
    return {
      value: '',
      fullName: fullName,
      fullHeight: fullHeight,
    };
  },
};
</script>
