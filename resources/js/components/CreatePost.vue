<template>
    <div class="container">
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="postTitle">Title</label>
          <input type="text" class="form-control" v-model="post.title" id="postTitle" placeholder="Enter post title" required>
        </div>
        <div class="form-group">
          <label for="postDescription">Description</label>
          <textarea class="form-control" v-model="post.description" id="postDescription" rows="3" placeholder="Enter post description" required></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios'; // Import axios correctly
  
  export default {
    data() {
      return {
        post: {
          title: '',
          description: ''
        }
      };
    },
    methods: {
      submitForm() {
        // Handle form submission logic here, for example, send the post data to the server
        console.log('Submitted Post:', this.post);
        
        axios.post('/posts', this.post)
          .then(response => {
            console.log(response.data);
          })
          .catch(error => {
            console.error('Error submitting post:', error);
          });
      }
    }
  };
  </script>
  
  <style scoped>
  /* Your scoped styles go here */
  </style>
  