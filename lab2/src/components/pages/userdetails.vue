<template>
  <div class="w-50" style="margin: 10px auto; padding: 5%;">
    <div class="card custom-card">
      <h1>User Details</h1>
      <hr/>
      <div>
        <p class="card-title">ID:{{ id }}</p>
        <p class="card-title">First Nmae:{{ first_name }}</p>
        <p class="card-title">Last Name{{ last_name }}</p>
        <p class="card-title">Gender: {{ gender }}</p>
        <button class="btn btn-primary" @click="back">Go to Users</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "userdetailsApp",
  data(){
    return{
        id:'',
        first_name:'',
        last_name:'',
        gender:''
    }
  },
  created(){
    this.getuserById()
  },
  methods:{
    getuserById(){
      this.id = this.$route.params.id;
      console.log(this.id)
      axios.get(` http://localhost:2000/users/${this.id}`)
      .then((res)=>{
        console.log(res.data)
        this.id = res.data.id
        this.first_name = res.data.first_name
        this.last_name = res.data.last_name
        this.gender = res.data.gender
      })
      .catch((err)=>console.log(err))
    },
    back(){
        this.$router.push('/users')
    }
  }
};
</script>

<style scoped>
.custom-card {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
  border-radius: 10px;
  padding: 20px;
}

.card-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.card-text {
  margin-bottom: 20px;
}


</style>
