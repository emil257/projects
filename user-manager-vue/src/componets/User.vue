<template>
  <div class="mt-2">
    <span v-if="editingID !== user.id" class="form-row">
      <button class="btn btn-danger btn-sm mr-2" @click="$emit('user-removed', user.id)">Remove</button>
      <button class="btn btn-outline-warning btn-sm mr-2" @click="$emit('set-user-edit-id', user.id)">Edit</button>
      <span>{{ user.name }}, Age: {{user.age}}, ID: #{{ user.id }}</span>
    </span>
    <my-edit-user 
      v-if="editingID === user.id" 
      :user="user" 
      @cancel-edit="$emit('cancel-edit', $event)"
      @user-edited="$emit('user-updated', $event)">
    </my-edit-user>
  </div>
</template>

<script>
import EditUser from './EditUser'

export default {
  props: [
    'user', 
    'editingID'
  ],
  components: {
    'my-edit-user': EditUser
  }
}
</script>
