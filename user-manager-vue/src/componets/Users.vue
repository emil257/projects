<template>
  <div>
    <my-add-user @user-added="addUser($event)"></my-add-user>
    <my-user 
      v-for="user in users" 
      :key="user.id"
      :user="user"
      :editingID="currentEditID"
      @user-removed="removeUser($event)"
      @user-updated="$emit('user-edited', updateUser($event))"
      @set-user-edit-id="setEditID($event)"
      @cancel-edit="currentEditID = 0">
    </my-user>
  </div>
</template>

<script>
import { uuid } from 'uuidv4';
import User from './User'
import AddUser from './AddUser'

export default {
  data(){
    return {
      currentEditID: 0,
      users: [
        {
          id: uuid(),
          name: 'John',
          age: 27
        }
        ,
        {
          id: uuid(),
          name: 'Anna',
          age: 33
        },
        {
          id: uuid(),
          name: 'Emil',
          age: 20
        }
      ]
    }
  },
  components:{
    'my-user': User,
    'my-add-user': AddUser
  },
  methods: {
    removeUser(id){
      for (let i = 0; i < this.users.length; i++) {
        if(this.users[i].id === id)
          this.users.splice(i, 1)
      }
      this.currentEditID = 0
    },
    addUser(user){
      this.users.push(user)
    },
    updateUser(user){
      for (let i = 0; i < this.users.length; i++) {
        if(this.users[i].id === user.id){
          this.users[i].name = user.name
          this.users[i].age = user.age
        }
      }
      this.currentEditID = 0
    },
    setEditID(id){
      this.currentEditID = id
    }
  }
}
</script>
