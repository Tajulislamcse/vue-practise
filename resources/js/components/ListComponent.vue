<template>
  <table>
    <tr>
        <th>Title</th>
        <th>Description</th>
        <th>Action</th>
    </tr>
    <tr v-for ="post in posts" :key="post.id">
     <td>{{ post.title }}</td>
     <td>{{ post.description }}</td>
     <td>
     <button  @click="deletePosts(post.id)">
      Delete
     </button>
    </td>
    </tr>
  </table>
</template>
<script>
import axios from 'axios';

export default {
    data(){
    return {
       posts : []
    }
},
methods:{
    deletePosts(id){
        axios.delete(`posts/${id}`)
        let index = this.posts.findIndex(post => post.id === id);
        this.posts.splice(index,1)

    }
},
mounted(){
    axios.get('posts')
    .then(response=>{
        this.posts = response.data.posts;
        console.log(this.posts)
    })
}
}


</script>
<style scoped>

</style>
