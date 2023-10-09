<template>
    <div class="table">

      <h1>Click to view photos for each album</h1>

      <table class="albums">
          <tbody class="album">

            <tr v-for="(album,index) in albums" :key="index">
              <td>
                <NuxtLink :to="`/albums/${album.id}`">{{ album.title }}</NuxtLink>
              </td>
            </tr>
          </tbody>
    
      </table>
    </div>
    </template>
    
    
    
    <script>
    import axios from 'axios'
    export default {
            data(){
                return {
                    albums:[],
                }
            },
    
    methods: {
                 async getAlbums(){
                    await axios.get(`https://jsonplaceholder.typicode.com/albums`,)
                    .then((res) =>
                    {   
                        this.albums = res.data;
                        console.log(this.albums);
                    });
                },
        },
        mounted(){
    
                this.getAlbums();
            }
    }
    </script>
    
    
    <style scoped>

    .table{
      margin-top: 100px;
    }

    .table h1{
      font-size: 30px;
      text-align: center;
      color: grey;
      margin-bottom: 10px;
    }
    .albums{
      width: 100%;
      text-align: center;
    }
    
    .album a{
        color: black;
        text-decoration: none;
        text-align: center;
        font-size: 20px;
        font-weight: 500;
        line-height: 50px;
      }

      .album a:hover{
        color: rgb(173, 157, 11);
        text-decoration: none;
        text-align: center;
        font-size: 20px;
        font-weight: 500;
        line-height: 50px;
      }
    </style>
    