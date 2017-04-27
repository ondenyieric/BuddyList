<template>
  <div class="col-md-3">
    
       <div class="list-group" v-for="task in tasks">

          <a href="#" class="list-group-item" >
            <h4 class="list-group-item-heading">
              <i class="glyphicon glyphicon-flag"></i> 
                    {{ task.name }}
            </h4>

            <h5>
              <i class="glyphicon glyphicon-calendar" ></i> 
                       {{ task.endtime }}
            </h5>

            <p class="list-group-item-text" >{{task.description}}</p>

            <button class="btn btn-xs btn-danger">Delete</button>
          </a>
          

      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'hello',
  data () {
  return {
     tasks:{
            name:'',
            description:'',
            endtime:''
      },
      task:[]
    }
  },
  created() {
        axios.get(`https://hazebuddylist.herokuapp.com/tasks`)
        .then(response => {
          // JSON responses are automatically parsed.
          this.tasks = response.data
    })
      .catch(e => {
        this.errors.push(e)
    })

    
  },
  methods()
  {
    
  }
}
</script>

<style>
</style>