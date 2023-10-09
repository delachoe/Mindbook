<template>
<div>
  <table class="posts">

      <tbody class="post">
        <tr v-for="(post,index) in posts" :key="index">
          <td>
              <h1>{{ post.title }}</h1>
              <p>{{ post.body }}</p>
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
                posts:[],
            }
        },

methods: {
             async getPosts(){
                await axios.get(`https://jsonplaceholder.typicode.com/posts/`,)
                .then((res) =>
                {   
                    this.posts = res.data;
                    console.log(res);
                });
            },
    },
    mounted(){

            this.getPosts();
        }
}
</script>


<style scoped>
.posts{
  margin-top: 80px;
}
  h1{
    color: black;
    text-align: center;
    font-size: 25px;
    line-height: 50px;
  }
   p{
    text-align: center;
    font-size: 20px;
   }
</style>
