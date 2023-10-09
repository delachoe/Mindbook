<template>
    <div class="form" >

            <h1> Login </h1>
            <form id="register" @submit.prevent="handleSubmit()">
                <input class="accounts" type="text" placeholder="Enter Username" v-model="username">
                <input class="accounts" type="password" placeholder="Enter Password" v-model="password">
                <div>
                <button>Login</button>
                </div>
            </form>

            <div  class="member">
                You Are Not A Member ? <NuxtLink to="/auth/register">Register</NuxtLink>
            </div>
    
     </div>
 </template>

<script>
import axios from 'axios'
 export default{
    data(){
       return {
            username : "",
            password : "",
            errors: []
        }
    },

    methods: {
    async handleSubmit() {
                await axios.post(`https://jsonplaceholder.typicode.com/users/`,{
                username: this.username,
                password : this.password
            },
            {
                    headers: {'Content-Type': 'application/json',
                    // Authorization : 'Bearer ' + localStorage.token,
                    'Access-Control-Allow-Origin': '*'
                },
                credentials: 'include',
                }).then((response) =>{  

                const token = response.data.access_token;
                alert("Login Successful");
                
                localStorage.setItem('token',token);
                
                this.$router.push('/posts')
                    
            });
        },       
        }
    }   
</script>


<style scoped>
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
        margin-top: 20px;
    }

    .member a{
        color: rgb(145, 6, 6);
    }
</style>