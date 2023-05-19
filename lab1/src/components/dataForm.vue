<template>
  <div>
    <div class="control-btns">
      <button @click="content='form'">Form</button>
      <button @click="content='adminTable'">Admins</button>
      <button @click="content='userTable'">Users</button>
    </div>

    <div class="container">
      <form class="form" v-show="content=='form'" @submit.prevent="formHandling">
        <h2 class="sub mb">Add new User/Admin</h2>
        <input v-model="formValues.id" type="number" class="input" placeholder="id"/>
        <input v-model="formValues.username" type="text" class="input" placeholder="username"/>
        <input v-model="formValues.email" type="email" class="input" placeholder="email"/>
        <input v-model="formValues.age" type="number" class="input" placeholder="age"/>

        <select v-model="formValues.role" name="role" class="input">
          <option value="" selected hidden>select role</option>
          <option value="admin">admin</option>
          <option value="user">user</option>
        </select>

        <button>Register</button>
      </form>

      <AdminsTable v-show="content=='adminTable'"  :admins="admins" @adminDeleted="handleAdminDeleted"/>
      <UsersTable v-show="content=='userTable'" :users="users" @userDeleted="handleUserDeleted"/>
    </div>
  </div>
</template>

<script>

import AdminsTable from "./adminsTable.vue";
import UsersTable from "./usersTable.vue";

export default {
  name: "DataForm",
  components: {
    AdminsTable,
    UsersTable,
  },
  data() {
    return {
      content: 'form',
      formValues: {
        id:'',
        username: '',
        email: '',
        age: '',
        role: '',
      },
      admins:[],
      users:[]
    };
  },
  methods:{
      formHandling() {
      if (this.formValues.role === 'admin') {
        this.admins.push({ ...this.formValues }); 
      } else {
        this.users.push({ ...this.formValues }); 
      }
      
      console.log('admins:'+JSON.stringify(this.admins));
      console.log('users:'+JSON.stringify(this.users));
    },
    handleAdminDeleted(updatedAdmins) {
      this.admins = updatedAdmins;
      console.log(this.admins);
    },
    handleUserDeleted(updatedUsers) {
      this.users = updatedUsers;
      console.log(this.users);
    },
  }
};
</script>


<style scoped>
.container{
  width:100%;
  display: flex;
  justify-content: center;
  margin-top: 5%;
}
.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 300px;
  background-color: #d4cff8;
  border-radius: 20px;
  padding: 30px 20px;
  box-shadow: 100px 100px 80px rgba(0, 0, 0, 0.03);
}

.title {
  color: black;
  font-weight: bold;
  text-align: center;
  font-size: 20px;
  margin-bottom: 4px;
}

.sub {
  text-align: center;
  color: black;
  font-size: 20px;
  width: 100%;
}

.sub.mb {
  margin-bottom: 5px;
  color: rgb(1, 47, 96);
}

.sub a {
  color: rgb(23, 111, 211);
}

.avatar {
  height: 50px;
  width: 50px;
  background-color: rgb(23, 111, 211);
  border-radius: 50%;
  align-self: center;
  padding: 6px;
  cursor: pointer;
  box-shadow: 12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
    100px 100px 80px rgba(0, 0, 0, 0.03);
}

.form button {
  align-self: flex-end;
}

.input,
button,select {
  border: none;
  outline: none;
  width: 80%;
  padding: 16px 10px;
  background-color: rgb(255, 252, 252);
  border-radius: 10px;
  box-shadow: 12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
    100px 100px 80px rgba(0, 0, 0, 0.03);
  margin: 2px auto;
}

button {
  margin-top: 12px;
  background-color: rgb(23, 111, 211);
  color: #fff;
  text-transform: uppercase;
  font-weight: bold;
}

.input:focus {
  border: 1px solid rgb(23, 111, 211);
}

.control-btns {
  display: flex;
  justify-content: space-around;
  width: 100%;
}

.control-btns button {
  width: 100px; 
}

button:hover {
  background-color: rgb(7, 61, 123); 
  cursor: pointer;
}
</style>
