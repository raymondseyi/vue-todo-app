<template>
    <div>
        <!-- <h4>Welcome,{{allUsers[signedInIndex].firstName}}</h4> -->
        <input type="text" placeholder="Enter Task" class="form-control my-2" v-model="task">
        <button class="btn btn-success my-2" @click="$emit('addTask',task)">Add Task</button>
        
        <div >
            <h4>List of Tasks</h4>
            <ol style="list-style-type: none;">
                <li class="my-4" v-for="(task,index) in currentUserTasksArray" :key="index"> 
                    <input type="checkbox" @click="$emit('taskDone',index)">
                    <span v-show="task.status==false">
                        {{task.task}}
                    </span>
                    <span  v-show="task.status==true">
                        <del>{{task.task}}</del>
                    </span>
                    <button class="btn btn-danger mx-2" @click="$emit('deleteTask',index)">x</button>
                </li>
            </ol>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            task:"",
            done:false,
        }
    },
    props:['currentUserTasksArray'],
    methods:{  
    }
}
</script>