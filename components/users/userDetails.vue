<template>
  <div>
    <div class="posts">
      <p v-if="loading">loading...</p>
      <div v-else class="post" >
          <div>
                  <p id="name">{{ profiles.name }}<br></p>
                  <p id="username">{{ profiles.username }}<br></p>
          </div>

            <div>
              <p id="email"> {{profiles.email}}</p>
              <p id="website">www.{{profiles.website}}</p>
            </div>
              
            <div class="company">
              <h1>Company Details</h1>
              <p id="cname">{{ profiles.company.name }}</p>
            <p id="cphrase">{{ profiles.company.catchPhrase }}</p>
            </div>

            <div>
              <button class="buttons" @click="toggle(profiles.id)">{{ isActive[profiles.id]? 'Decline':'Accept'}}</button>
            </div>
          </div>
      </div>
  </div>
</template>


<script>
import axios from 'axios'
export default {
        data(){
            return {
              
                userId:'',
                profiles:{},
                isActive:{},
                loading:false

            }
        },

methods: {  
            toggle(profileId){
              this.isActive[profileId] = !this.isActive[profileId];
            },

            async getUser(){
                this.loading=true;
                await axios.get(`https://jsonplaceholder.typicode.com/users/${this.userId}`,
                {
                    headers:{"Content-Type": "application/json",
                    // Authorization : 'Bearer' + localStorage.token,
                    'Access-Control-Allow-Origin': '*'
                },
                }).then((res) =>
                {   
                    this.profiles = res.data;
                    console.log(res);
                }).finally(()=>{
                  this.loading = false
                });
            },
    },
    beforeMount(){
            this.userId = this.$route.params.id;
            this.getUser(this.$route.params.id);
    },
    mounted(){
           
        }
}
</script>




<style scoped>
    .posts{
        width: 99%;
        height: 100vh;
        background-color:#ffffff;
        text-align: center;
        border-collapse:collapse;
        margin-top: 140px;
    }

    #email{
      font-size: 25px;
    }

    #website{
      font-size: 25px;
    }
    

    #name{
        color: black;
    }

    #username{
        font-size: 25px;
        color: black;
    }

    p{
      font-size:30px;
    }

    .company{
      margin-top: 60px;
    }
    #cname{
      font-size: 30px;
    }

    #cphrase{
      font-size: 20px;
      font-weight: 400;
    }

    #bs{
      font-size: 15px;

    }

    .post button{
      background-color: black;
      border: none;
      padding: 10px 20px;
      color: #ffffff;
      width: 120px;
      border-radius: 10px;
      transition: all 0.3s ease-in;
      margin-top: 60px;
    }

    .post button:hover{
        color: black;
        border:2px solid black;
        background-color: white;
    }

</style>