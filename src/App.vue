<template>
  <div id="app">
  <div class="row">
     <tech></tech>
     <business></business>
     <comms></comms>
     <capstone></capstone>
     </div>
      <!-- <div class="row">
     <taskManager></taskManager>
     </div>-->
       <div class="row">
     <reminder></reminder>
     <hello></hello>
     <noticeBoard></NoticeBoard>
     </div>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Tech from './components/Tech'
import Comms from './components/Comms'
import Business from './components/Business'
import Capstone from './components/Capstone'
import TaskManager from './components/TaskManager'
import Reminder from './components/Reminder'
import NoticeBoard from './components/NoticeBoard'

export default {
  name: 'app',
  components: {
    Hello,
    Tech,
    Comms,
    Business,
    Capstone,
    TaskManager,
    Reminder,
    NoticeBoard,

  }
}
</script>

<style>

</style>
