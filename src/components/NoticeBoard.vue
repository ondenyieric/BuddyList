<template>
<div>
<div class="col-md-6">
<div class="panel panel-info">
  <!-- Default panel contents -->
  <div class="panel-heading"><i class="glyphicon glyphicon-globe"> </i> General Board</div>

  <!-- Table -->
  <table class="table" v-if="notices && notices.length" >
    <paginate name="notices" :list="notices" class="paginate-list">
    <tr >
     	<td v-for="notice of notices">  
       
        <img :src= notice.url width="150px">
        <div>
        <span>{{ notice.description  }}</span><br/>
        <span>{{ notice.postedBy     }}</span><br/>
        <span>{{ notice.eventTime    }}</span>
        </div>
         
    	</td>
      </tr>
      </paginate>
  </table>
</div>
</div>
<paginate-links for="notices" :simple="{
        next: 'Next »',
        prev: '« Back'
      }"></paginate-links>

</div>
</template>
<script>
import axios from 'axios';
import VuePaginate from 'vue-paginate';



export default {
  name: 'noticeBoard',
 data () {
    return {
      notices: {
      url:'',
      description:'',
      postedBy:'',
      eventTime:'',
      created_at:'',
      updated_at:'',
      },
      notice: [],
       paginate: ['notices']
     }

    },
    created() {
		    axios.get(`https://hazebuddylist.herokuapp.com/notices`)
		    .then(response => {
		      // JSON responses are automatically parsed.
		      this.notices = response.data
    })
	    .catch(e => {
	      this.errors.push(e)
    })

    
  }

}
</script>






<style scoped>

.paginate-list {
  width: 159px;
  margin: 0 auto;
  text-align: left;
  li {
    display: block;
    &:before {
      content: '⚬ ';
      font-weight: bold;
      color: slategray;
    }
  }
}

.paginate-links.items {
  user-select: none;
  a {
    cursor: pointer;
  }
  li.active a {
    font-weight: bold;
  }
  li.next:before {
    content: ' | ';
    margin-right: 13px;
    color: #ddd;
  }
  li.disabled a {
    color: #ccc;
    cursor: no-drop;
  }
}

a {
  color: #42b983;
}

</style>