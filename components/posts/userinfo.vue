<!-- <template>
        <div  class="user-info" v-for="user in users" :key="user.id">
            <h1 class="username">{{ user.name }} <br></h1>
            <div>
            <button>View Profile</button>
            </div>
        </div>

</template>

  <style scoped>
    .feed{
        width: 100vw;
        height: 100vh;
        background-color: palevioletred;
        top: 0;
    }
    .posts{
        width: 60vw;
        height: 100vh;
        background-color:#ffffff;
        margin-left: 250px;
        border-collapse: collapse;
    }

    .post td{
        font-size:10px;
        text-align: center;
    }

    .username{
        text-align: left;
    }

</style>



<script>
import axios from 'axios'
export default {
        data(){
            return {
                userId:'',
                posts:[],
                users:[],
            }
        },

methods: {
             async getPosts(){
                await axios.get(`https://jsonplaceholder.typicode.com/posts/${this.userId}`,this.posts)
                .then((res) =>
                {   
                    this.posts = res.data;
                    console.log(this.posts);
                });
            },

            async getUsers(){
                await axios.get(`https://jsonplaceholder.typicode.com/users`,
                {
                    headers:{"Content-Type": "application/json",
                    // Authorization : 'Bearer' + localStorage.token,
                    'Access-Control-Allow-Origin': '*'
                },
                }).then((res) =>
                {   
                    this.users = res.data;
                    console.log(this.users);
                });
            },

       
    },
    mounted(){
            this.getPosts();
            this.getUsers();
        }
}
</script>
        <table class="posts">

            <tbody class="post">
                <tr v-for="(user,index) in users" :key="index">
                    <td>
                        <div  class="user-info">
                            <h1 class="username">{{ user.name }} <br></h1>
                            <h1 class="username">{{ user.username }} <br></h1>

                            <div v-for="(post,index) in posts" :key="index">
                                <h1>{{ post.title }}</h1>
                                <p>{{ post.body }}</p>
                            </div>
                        </div>

                    </td>
                </tr>
            </tbody>

        </table>

<script>
import axios from 'axios'
    export default {

        props: {
            postId: {
            type: Number,
            required: true,
            },
        },

        data(){
            return {
                users:[],
        };
    },

        methods: {
                     async getUsersData(){
                        await axios.get(`https://jsonplaceholder.typicode.com/users`,
                        {
                            headers:{"Content-Type": "application/json",
                            // Authorization : 'Bearer' + localStorage.token,
                            // 'Access-Control-Allow-Origin': '*'
                        },
                        }).then((res) =>
                        {   
                            this.$emit('users-fetched',this.users);
                            this.users = res.data;
                            console.log(this.users);
                        });
                    },

               
            },
            mounted(){
                    this.getUsersData();
                }
    }
</script>



<style scoped>
    .user-info{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

     h1{
        font-size: 20px;
        color: black;
        font-weight: 700;
        line-height: 1rem;
    }

    span{
        font-size: 20px;
        align-items: left;
        color: black;
        line-height: 1rem; 
    }
</style> -->
