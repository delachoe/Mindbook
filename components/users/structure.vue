<template>
    <div>
        <NuxtLayout name="feed"/>
    </div>

    <div class="cards">
        <div v-for="(user,index) in users" :key="index" class="column">
            <h1 id="name">{{ user.name }}<br></h1>
            <p id="username">{{ user.username }}<br></p>
            <NuxtLink :to="`/users/${user.id}`"><button>View Profile</button></NuxtLink>
        </div>
    </div>
</template>



<script>
    import axios from 'axios'
    export default {
            data(){
                return {
                    users:[],
                }
            },
    
    methods: {
                 async getUsers(){
                    await axios.get(`https://jsonplaceholder.typicode.com/users`,)
                    .then((res) =>
                    {   
                        this.users = res.data;
                        console.log(res);
                    });
                },
        },
        mounted(){
                this.getUsers();
            }
    }
    </script>


<style scoped>

    .cards{
        margin-top: 60px;
        display:flex;
        flex-wrap: wrap;
        width: 100%;
        text-align: center;
        background-color: black;
    }

    .column{
        width: 315px;
        height: 210px;
        margin: 10px;
        margin-top: 40px;
        background-color: rgb(255, 255, 255);
        border-radius: 10px;

    }

    .column h1{
        margin-top: 40px;
        font-size: 25px;
    }

    .column p{
        font-size: 23px;
    }

    .column button{
        margin-top: 40px;
        font-size: 15px;
        color:black;
        background-color: white;
        padding: 10px 20px;
        border: 1px solid black;
    }

    .column button:hover{
        margin-top: 40px;
        font-size: 15px;
        color:white;
        background-color: rgb(85, 6, 6);
        padding: 10px 20px;
        border: 1px solid rgb(126, 7, 7);
    }

</style>