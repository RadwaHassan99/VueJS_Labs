<template>
  <div class="mt-5 p-5">
    <div class="table-container w-75" style="margin: 0 auto;">
      <h1 class="p-3">Users Table</h1>
      <table class="table table-bordered table-shadow">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">First Name</th>
            <th scope="col">Last Name</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <th scope="row">{{ user.id }}</th>
            <td>{{ user.first_name }}</td>
            <td>{{ user.last_name }}</td>
            <td class="d-flex gap-3 justify-content-center">
              <button class="btn btn-sm btn-danger" @click="deleteUser(user.id)">delete</button>
              <button class="btn btn-sm btn-primary text-center"><router-link :to="`/user/${user.id}`" class="show">see more</router-link></button>
              <button class="btn btn-sm btn-success text-center"><router-link :to="`/user/${user.id}/update`" class="show">update</router-link></button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div> 
</template>

<script>
import axios from "axios";
export default {
  name: "allusersApp",
  created() {
    this.getallusers();
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    getallusers() {
      axios
        .get("  http://localhost:2000/users")
        .then((res) => {
          console.log(res.data);
          this.users = res.data
        })
        .catch((err) => console.log(err));
    },
    deleteUser(id){
        axios.delete(`  http://localhost:2000/users/${id}`)
        .then((res)=>{
            console.log(res.data)
            this.getallusers()
        })
        .catch((err)=>console.log(err))
    }
  },
};
</script>

<style scoped>  .table-container {
  padding: 10px;
  border: 1px solid #dee2e6;
  background-color: rgb(222, 232, 255);
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.show{
  text-decoration: none;
  color: white;
  text-align: center;
}
.table {
  width: 100%;
  border-collapse: collapse;
}

.table thead th {
  background-color: #f8f9fa;
  font-weight: bold;
  padding: 10px;
  text-align: center;
}

.table tbody td {
  padding: 10px;
  text-align: center;
}

.table tbody tr:nth-child(even) {
  background-color: #f8f9fa;
}

.table tbody tr:hover {
  background-color: #f1f3f5;
}

</style>
