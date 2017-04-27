<template>
<div class="container">
  <ul class="nav nav-pills" role="tablist">
	  <li role="presentation" class="active"><a href="#">Tasks <span class="badge">42</span></a></li>
	  <li role="presentation"><a href="#">Messages <span class="badge">3</span></a></li>
 </ul>


 </div>
</template>


<script>
import axios from 'axios';

export default {
  name: 'taskManager',
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

    
  }
}
</script>

<style>
</style>
