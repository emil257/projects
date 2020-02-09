<template>
  <div class="mt-3 mb-3">
    <form class="form-row" v-on:submit.prevent="$emit('user-added', constructUser(name, age))">
      <span class="mr-2">Name: </span>
      <input 
        type="text" 
        class="form-control form-control-sm col-3" 
        v-model="name" 
        @focus="name = ''">
      <span class="mr-2 ml-3">Age: </span>
      <input 
        type="number" 
        class="form-control form-control-sm col-1 mr-2" 
        v-model="age"
        @focus="age = ''">
      <button type="submit" class="btn btn-success btn-sm">Add</button>
    </form>
  </div>
</template>

<script>
import { uuid } from 'uuidv4';

export default {
  data(){
    return {
      name: 'Enter a name...',
      age: 0
    }
  },
  methods: {
    constructUser(_name, _age){
      return {id: uuid(), name: _name, age: _age}
    }
  }
}
</script>

<style>

</style>