<template>
    <div class="header">
        <div class="topnav">
            <img src="@/assets/chess2.jpg" alt="smiley emoji">
            <h1>WealthClub</h1>
        <ul class="links">
            <li><NuxtLink to="/users"> Members</NuxtLink>  </li>
            <li><NuxtLink to="/posts"> Advice</NuxtLink> </li>
            <li><NuxtLink to="/albums">Albums</NuxtLink>  </li>
        </ul>

       <NuxtLink to="/"><button>Exit</button></NuxtLink>
    </div>
    </div>
</template>



<style>
    .header{
        background-color: black;
        box-sizing: border-box;
        position: fixed;
        overflow: hidden;
        width: 100%;
        top:0;
        left:0;
    }

    .topnav img{
        height: 50px;
        border-radius: 30px;
    }

    li,a,button{
        font-weight: 500;
        font-size: 25px;
        color:rgb(236, 234, 234);
        text-decoration: none;
    }

    .topnav{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 10px 8%;
    }

    .topnav h1{
        font-size: 30px;
        cursor: pointer;
        color:rgb(236, 234, 234);
        margin-left: -15%;
    }

    .links{
        list-style: none;
    }

    .links li{
        display: inline-block;
        padding:0px 20px;
    }

    .links li a{
        transition: all 0.3s ease 0s;
    }

    .links li a:hover{
        color: grey;
    }

    button{
      background-color: black;
      border: solid 1px white;
      padding: 5px 20px;
      color: #ffffff;
      width: 120px;
      border-radius: 10px;
      transition: all 0.3s ease-in;
    }

    button:hover{
        color: white;
        border:2px solid rgb(145, 6, 6);
        background-color: rgb(145, 6, 6);
    }
</style>
