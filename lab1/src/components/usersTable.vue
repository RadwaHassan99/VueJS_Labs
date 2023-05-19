<template>
    <div>
        <table id="users">
  <tr>
    <th>ID</th>
    <th>Username</th>
    <th>Email</th>
    <th>Age</th>
    <th>Action</th>
  </tr>
  <tr v-for="user in users" :key="user.id">
    <td>{{user.id}}</td>
    <td>{{user.username}}</td>
    <td>{{user.email}}</td>
    <td>{{user.age}}</td>
    <td><button @click="deleteUser(user); $emit('userDeleted', usersCopy)">✖</button></td>  </tr>

</table>
    </div>
</template>

<script>
    export default {
        name:'UsersTable',
        props: ["users"],
        emits:['userDeleted'],
data(){
    return{
        usersCopy:this.users
    }

},
  methods: {
    deleteUser(user) {
      const index = this.usersCopy.indexOf(user);
      if (index !== -1) {
        this.usersCopy.splice(index, 1);
      }
    },
  },
};
</script>

<style scoped>
#users {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#users td, #users th {
  border: 1px solid #ddd;
  padding: 20px;
}

#users tr:nth-child(even){background-color: #f2f2f2;}

#users tr:hover {background-color: #ddd;}

#users th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #9a93cd;
  color: white;
}
button {
  background-color: red;
  border: 1px solid red;
  padding: 5px 5px;
  font-weight: bold;
  color: white;
  box-shadow: 100px 100px 80px rgba(0, 0, 0, 0.03);
}

button:hover {
  transform: scale(1.2);
  background-color: rgb(178, 4, 4);
  cursor: pointer;
}
</style>