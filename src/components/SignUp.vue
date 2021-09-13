<template>
    <div>
        <h4>Sign Up</h4>
        <input type="text" class="form-control my-2" placeholder="First Name" v-model="firstName">
        <input type="text" class="form-control my-2" placeholder="Last Name" v-model="lastName">
        <input type="text" class="form-control my-2" placeholder="Phone Number" v-model="phoneNumber">
        <input type="text" class="form-control my-2" placeholder="Email" v-model="email">
        <input type="text" class="form-control my-2" placeholder="Password" v-model="password">
        <button @click="addUser" class="btn btn-success my-2">Sign Up</button>
    </div>
</template>
<script>
export default {
    data(){
        return{
            firstName:"",
            lastName:"",
            phoneNumber:"",
            email:"",
            password:"",
            tasks:[] 
        }
    },
    methods:{
        addUser(){
            let {firstName,lastName,phoneNumber,email,password,tasks}=this
            let user={firstName,lastName,phoneNumber,email,password,tasks}
            this.$emit('joinUser',user)
        }
    }
}
</script>