<template>
  <div>
    <table id="admins">
      <tr>
        <th>ID</th>
        <th>Username</th>
        <th>Email</th>
        <th>Age</th>
        <th>Action</th>
      </tr>
      <tr v-for="admin in adminsCopy" :key="admin.id">
        <td>{{ admin.id }}</td>
        <td>{{ admin.username }}</td>
        <td>{{ admin.email }}</td>
        <td>{{ admin.age }}</td>
        <td><button @click="deleteAdmin(admin); $emit('adminDeleted', adminsCopy)">✖</button></td>
      </tr>
      
    </table>
  </div>
</template>

<script>
export default {
  name: "AdminsTable",
  props: ["admins"],
  emits:['adminDeleted'],
data(){
    return{
        adminsCopy:this.admins
    }

},
  methods: {
    deleteAdmin(admin) {
      const index = this.adminsCopy.indexOf(admin);
      if (index !== -1) {
        this.adminsCopy.splice(index, 1);
      }
    },
  },
};
</script>

<style scoped>
#admins {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#admins td,
#admins th {
  border: 1px solid #ddd;
  padding: 20px;
}

#admins tr:nth-child(even) {
  background-color: #f2f2f2;
}

#admins tr:hover {
  background-color: #ddd;
}

#admins th {
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