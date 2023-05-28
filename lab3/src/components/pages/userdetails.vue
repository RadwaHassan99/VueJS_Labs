<template>
  <div class="w-25" style="margin: 10px auto; padding-top: 15%;">
    <div class="card custom-card">
      <h1>User Details</h1>
      <hr/>
      <div>
        <p class="card-title">ID:{{ user.id }}</p>
        <p class="card-text"><strong>First Name:</strong>{{ user.first_name }}</p>
        <p class="card-text"><strong>Last Name:</strong>{{ user.last_name }}</p>
        <p class="card-text"><strong>Gender:</strong> {{ user.gender }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { ref,reactive } from 'vue';
import { useRoute } from 'vue-router';

export default {
  name: "userdetailsApp",
  setup() {

    const route =useRoute();

    const user = reactive({
      first_name: ref(""),
      last_name: ref(""),
      gender: ref("")
    });

    const getuserById = async () => {
      try {
        user.id = route.params.id;
        const response = await axios.get(`http://localhost:2000/students/${user.id}`);
        const { data } = response;
        user.first_name = data.first_name;
        user.last_name = data.last_name;
        user.gender = data.gender;
      } catch (error) {
        console.log(error);
      }
    };

    getuserById();

    return {
      user
    };
  },
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
