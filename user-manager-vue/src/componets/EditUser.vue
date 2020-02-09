<template>
  <form class="form-row" v-on:submit.prevent="$emit('user-edited', constructUser(name, age))">
    <button type="button" class="btn btn-outline-warning btn-sm mr-2" @click="$emit('cancel-edit', user)">Cancel</button>
    <input type="text" class="ml-1 form-control form-control-sm col-3" v-model="name" placeholder="Enter a name...">
    <span class="mr-2 ml-3">Age: </span>
    <input type="number" class="form-control form-control-sm col-1 mr-2" v-model="age">
    <button type="submit" class="btn btn-success btn-sm">Update</button>
  </form>
</template>

<script>
export default {
  props: [
    'user'
  ],
  data(){
    return {
      name: this.user.name,
      age: this.user.age
    }
  },
  methods: {
    constructUser(_name, _age){
      return {id: this.user.id, name: _name, age: _age}
    }
  }
}
</script>