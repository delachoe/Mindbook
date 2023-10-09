<template>
    <div class="form">

            <h1> Register </h1>
            <form id="register" @submit.prevent="addNewUser()">
                <input class="accounts" type="text" placeholder="Enter Username" v-model="username">
                <input class="accounts" type="password" placeholder="Enter Password" v-model="password">
                <input class="accounts" type="password" placeholder="Confirm Password" v-model="cpassword">
                <div>
                <button>Register</button>
                </div>
            </form>

            <div  class="member">
                Already A Member? <NuxtLink to="/auth/login">Login</NuxtLink>
            </div>
    
     </div>
 </template>
 
 <script scoped>   
 import axios from 'axios'
 export default{
    data(){
       return {
            username : "",
            password : "",
            cpassword : "",

        }
    },

    methods: {
    async addNewUser() {
                await axios.post(`https://jsonplaceholder.typicode.com/users/`,{
                username: this.username,
                password : this.password
            },{
                    headers: {'Content-Type': 'application/json',
                   //Authorization : 'Bear' + localStorage.token
                    'Access-Control-Allow-Origin': '*'
                },
                credentials: 'include',
                }).then((response) =>{  

                const data = response.data;
                alert("User Added Successfully");
                console.log(response);

                if(response.status === 200){
                    this.$router.push('/auth/login')
                }

                else{
                    console.error('Registration Failed',response.data)
                }
        });
     
    }   
    },
 
 }
 </script>

 <style scoped >
    .form{
        margin-top: 100px;
        width:330px;
        padding:4rem 2rem;
        margin-left: 500px;
        background-color:white;
        border-radius: 10px;
        text-align: center;
        box-shadow: 0 20px 35px rgb(0, 0,0.1);
    }

    h1{
        font-size: 2.5rem;
        margin-bottom: 1.9rem;
    }

    form input{
        width: 92%;
        outline: none;
        border : 1px solid rgb(151, 140, 140);
        padding: 12px 15px;
        margin-bottom: 10px;
        border-radius: 20px;
    }

    button{
        font-size: 1rem;
        margin-top: 1.8rem;
        padding: 10px 0;
        width: 90%;
        border: none;
        border-radius: 20px;
        outline: none;
        background-color: rgb(145, 6, 6);
        color:white;
        }

    .member{
            color:rgb(145, 6, 6);
            text-decoration: none;
            margin-top: 1.4rem;
            font-size: 18px;
        }

    .member a{
            color:rgb(145, 6, 6);
            text-decoration: none;
            font-weight: 900;
        }

</style>