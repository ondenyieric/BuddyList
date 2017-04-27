<template>
<!-- add an event form -->
    <div class="col-sm-3">
      <div class="panel panel-primary">
        <div class="panel-heading">
          <h3>Capstone</h3>
     
        </div>
        <div class="panel-body">
           <ul class="list-group" v-for="n in news">
               <li class="list-group-item"> <span >{{n.subject}}</span> <span class="badge">urgent</span></li>
           </ul>
        </div>

      </div>
    </div>
</template>


<script>
import axios from 'axios';

export default {
  name: 'capstone',
  data () {
    return {
       news:{
            description:'',
            subject:''
      },
      new:[]
    }
  },

  created() {
        axios.get(`https://hazebuddylist.herokuapp.com/news`)
        .then(response => {
          // JSON responses are automatically parsed.
          this.news = response.data
    })
      .catch(e => {
        this.errors.push(e)
    })

    
  }
}
</script>



<style>
</style>