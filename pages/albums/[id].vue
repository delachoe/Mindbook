<template>
    <div>
        <NuxtLayout name="feed"/>
    </div>

    <div class="container">
        <div v-for="(photo,index) in photos" :key="index" class="column">
            <img :src="photo.url"  loading="lazy" alt="" class="image"><br>
            <span>{{ photo.title }}</span>
        </div>
    </div>
</template>



<script>
    import axios from 'axios'
    export default {
            data(){
                return {
                    albumId:'',
                    photos:[],
                }
            },
    
    methods: {
                 async getPhotos(){
                    await axios.get(`https://jsonplaceholder.typicode.com/photos?albumId=${this.$route.params.id}`,)
                    .then((res) =>
                    {   
                        this.photos = res.data;
                        console.log(res);
                    });
                },
        },
        mounted(){
              console.log(this.$route.params.id);
                this.getPhotos();
            }
    }
    </script>


<style scoped>
    .container{
        margin-top: 110px;
        display:flex;
        flex-wrap: wrap;
        width: 100%;
        text-align: center;
    }

    .column{
        width: 425px;
        height: 210px;
        margin:10px;
    }

    .column .image{
        height: 160px;
        margin-bottom: 8px;
    }

</style>