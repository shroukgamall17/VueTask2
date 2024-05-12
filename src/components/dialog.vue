<template>
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Add Student</h5>
        <button type="button" class="close" @click="cancel">&times;</button>
      </div>
      <div class="modal-body">
        <form @submit="addStudent">
          <div class="form-group">
            <label for="studentId">ID:</label>
            <input type="text" class="form-control" id="studentId" v-model="newStudent.id">
          </div>
          <div class="form-group">
            <label for="studentName">Name:</label>
            <input type="text" class="form-control" id="studentName" v-model="newStudent.name">
          </div>
          <div class="form-group">
            <label for="studentCity">City:</label>
            <input type="text" class="form-control" id="studentCity" v-model="newStudent.city">
          </div>
          <button type="submit" class="btn btn-primary">Add</button>
          <button type="button" class="btn btn-secondary" @click="cancel">Cancel</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newStudent: {
        id: '',
        name: '',
        city: ''
      }
    };
  },
  methods: {
    addStudent() {
      this.$emit('add', this.newStudent);
      this.newStudent = { id: '', name: '', city: '' }; 
    },
    cancel() {
      this.$emit('cancel');
      this.newStudent = { id: '', name: '', city: '' }; 
    }
  }
};
</script>

<style>

</style>
