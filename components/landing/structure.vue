<template>

    <div class="wrap">
        <h1>Meet The Billioniares</h1>
        <NuxtLink to="/auth/login">Welcome</NuxtLink>
    </div>

</template>



<style scoped>
    .wrap{
        background-image:url("@/assets/chess2.jpg");
        background-color: black;
        background-repeat: no repeat;
        background-size: cover;
        background-position: center;
        height:100vh;
    }

    .wrap h1{
        font-family:'Times New Roman', Times, serif;
        text-align: right;
        margin-right: 350px;
        padding-top: 40vh;
        font-size: 4rem;
        color: white;
        letter-spacing: 3px;
    }

    .wrap a{
        display: block;
        margin: 30px 750px;
        padding: 10px 100px;
        color:black;
        border: 2px solid white;
        border-radius: 35px;
        background-color: rgb(248, 248, 248);
        font-size:15px;
        font-weight: bold;
        text-decoration: none;
        letter-spacing:2px;
    }

    .wrap a:hover{
        color: white;
        border:2px solid black;
        background-color: black;
    }
</style>