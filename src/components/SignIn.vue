<template>
    <div>
        <h4>Sign In</h4>
        <input type="text" class="form-control my-2" placeholder="Email" v-model="email">
        <input type="text" class="form-control my-2" placeholder="Password" v-model="password">
        <button @click="signIn" class="btn btn-success my-2">Sign In</button>
    </div>
</template>
<script>
export default {
    data(){
        return{
            email:"",
            password:"",
        }
    },
    methods:{
        signIn(){
            let {allUsers,email,password}=this
            let found=allUsers.find((val)=>val.email==email&&val.password==password)
            if(found){
                alert('O boy, you don log in o')
                let userIndex=allUsers.indexOf(found)
                console.log(userIndex);
                this.$emit('getIndex',userIndex)
            }
            else{
                alert('invalid details')
            }
            console.log(found);
        }
    },
    props:['allUsers']
}
</script>