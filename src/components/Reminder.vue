<template>
<div>
    <div class="col-md-3">
     <div class="panel panel-info">
      <div class="panel-heading">
      Add your personal tasks
      </div>
      <div class="panel-body">

        <div class="form-group">
          <input class="form-control" placeholder="Task Name" v-model="postBody.name" >
        </div>

        <div class="form-group">
          <textarea class="form-control" placeholder="Task Description" v-model="postBody.description"></textarea>
        </div>

        <div class="form-group">
          <input type="date" class="form-control" placeholder="Date" v-model="postBody.endtime">
        </div>

        <button type="submit" class="btn btn-default" v-on:click="postPost">Add1</button>

      </div>
    </div>
 </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'reminder',
  data: () => ({
    postBody: { name:this.name,
                description:this.description,
                endtime:this.endtime
    },
    errors: []
  }),
    methods: {
  // Pushes posts to the server when called.
  postPost() {
  console.log(this.postBody);
    axios.post(`https://hazebuddylist.herokuapp.com/tasks`, 
      {        name: this.postBody.name,
                description: this.postBody.description,
                endtime: this.postBody.endtime
               })
    .then(response => {})
    .catch(e => {
      this.errors.push(e)
    })
 }
}
}
</script>

<style>
</style>