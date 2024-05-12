<template>
  <div class="col-9">
    <add-student-dialog v-if="showDialog" @add="addStudent" @cancel="cancelAdd"></add-student-dialog>
    <div class="table-responsive"> 
      <table class="table table-striped table-bordered text-center"> 
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>City</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="student in students" :key="student.id">
            <td>{{ student.id }}</td>
            <td>{{ student.name }}</td>
            <td>{{ student.city }}</td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <th colspan="3">No. of students = {{ students.length }}</th>
          </tr>
        </tfoot>
        
      </table>
    <button class="btn btn-danger my-2" @click="showDialog = true">Add new Student</button>

    </div>
  </div>
</template>

<script>
import students from '../students'
import AddStudentDialog from './dialog.vue';

export default {
  data() {
    return {
      students: students,
      showDialog: false
    };
  },
  components: {
    AddStudentDialog
  },
  methods: {
    addStudent(newStudent) {
      this.students.push(newStudent);
      this.showDialog = false; 
    },
    cancelAdd() {
      this.showDialog = false; 
    }
  }
};
</script>

<style>

</style>
