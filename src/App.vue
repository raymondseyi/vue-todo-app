<template>
  <div class="container-">
    <div class="row">
      <div class="col-4 border-right mx-auto">
        <SignUp @joinUser="registerUser"/>
      </div>
      <div class="col-4 border-right">
        <SignIn :allUsers="allUsers" @getIndex="setIndex"/>
      </div>
      <div class="col-4">
        <User @addTask="addTasks" :currentUserTasksArray="currentUserTasksArray" @taskDone="taskDone" @deleteTask="deleteTask"/>
      </div>
    </div>
  </div>
</template>

<script>
import SignUp from "./components/SignUp.vue"
import SignIn from "./components/SignIn.vue"
import User from "./components/User.vue"
export default {
  
  name: 'App',
  data(){
    return{  
      allUsers:[],
      signedInIndex:"",
      currentUserTasksArray:[]
    }
  },
  components:{SignUp,SignIn,User},
  methods:{
    registerUser(user){
            this.allUsers= [...this.allUsers,user]
        },
    setIndex(userIndex){
      this.signedInIndex=userIndex
    },
    addTasks(task){
            this.allUsers[this.signedInIndex].tasks.push({task,status:false})
            this.currentUserTasksArray=this.allUsers[this.signedInIndex].tasks
        },
    taskDone(index){
      this.allUsers[this.signedInIndex].tasks[index].status=!this.allUsers[this.signedInIndex].tasks[index].status;
    },
    deleteTask(index){
      this.allUsers[this.signedInIndex].tasks = this.allUsers[this.signedInIndex].tasks.filter((_,i)=>i!=index)
      this.currentUserTasksArray=this.allUsers[this.signedInIndex].tasks  
      console.log(this.allUsers[this.signedInIndex].tasks);
    }
  },
}
</script>

