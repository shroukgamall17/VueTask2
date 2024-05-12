<template>
  <div>
    <div class="post-form" v-if="!submitted">
     
      <input v-model="title" placeholder="Title" class="input-title">
    
     
      <div class="category-radio">
        <div v-for="category in postdata.category" :key="category">
          <input type="radio" v-model="selectedCategory" :value="category" class="radio-input">
          <label>{{ category }}</label>
        </div>
      </div>
    
      
      <select v-model="selectedSeries" class="select-series">
        <option v-for="series in postdata.series" :key="series">{{ series }}</option>
      </select>
    

      <div class="social-networks-checkbox">
        <div v-for="network in postdata.socialnetworks" :key="network">
          <input type="checkbox" v-model="selectedSocialNetworks" :value="network" class="checkbox-input">
          <label>{{ network }}</label>
        </div>
      </div>
   
      <div class="publish-checkbox">
        <input type="checkbox" v-model="publishNow" class="checkbox-input">
        <label>Publish Now</label>
      </div>
    
 
      <button @click="submitForm" class="submit-button">Submit</button>
    </div>
     <div v-else>
        <h2>Submitted Data:</h2>
        <p>Title: {{ title }}</p>
        <p>Selected Category: {{ selectedCategory }}</p>
        <p>Selected Series: {{ selectedSeries }}</p>
        <p>Selected Social Networks: {{ selectedSocialNetworks.join(', ') }}</p>
        <p>Publish Now: {{ publishNow ? 'Yes' : 'No' }}</p>
        <div class='d-flex gap-3 align-items-center justify-content-center'>
            <button class='btn btn-success' @click="showSuccessAlert">ok</button>
            <button class='btn btn-danger' @click="cancel">cancel</button>
        </div>
      </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2';
export default {
  data() {
    return {
      title: '',
      selectedCategory: '',
      selectedSeries: '',
      selectedSocialNetworks: [],
      publishNow: false,
       submitted: false,
      postdata: {
        category: ["design", "network", "database", "development"],
        series: ["first", "second", "third"],
        socialnetworks: ["facebook", "X", "youtube", "instagram"]
      }
    };
  },
  methods: {
    submitForm() {
   this.submitted = true;
    }, cancel() {
      this.submitted = false;
    },
       showSuccessAlert() {
      Swal.fire({
        icon: 'success',
        title: 'Success',
        text: 'Data added successfully!',
        confirmButtonText: 'OK'
      });
    }
  }
};
</script>

<style scoped>
.post-form {
  max-width: 600px;
  margin: 0 auto;
}

.input-title {
  width: 100%;
  margin-bottom: 15px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.category-radio {
  margin-bottom: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.category-radio label {
  margin-right: 10px;
}

.select-series {
  width: 100%;
  margin-bottom: 15px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.social-networks-checkbox {
  margin-bottom: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.publish-checkbox label {
  margin-left: 5px;
}

.submit-button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
}

.submit-button:hover {
  background-color: #45a049;
}
</style>
