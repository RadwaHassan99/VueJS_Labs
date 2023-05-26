<template>
    <div class="mask d-flex align-items-center h-100 gradient-custom-3 mt-5 p-5">
      <div class="container h-100">
        <div class="row d-flex justify-content-center align-items-center h-100">
          <div class="col-12 col-md-9 col-lg-7 col-xl-6">
            <div class="card" style="border-radius: 15px">
              <div class="card-body p-5">
                <h2 class="text-uppercase text-center mb-5">Update User</h2>
  
                <form @submit.prevent="updateUser">
                  <div class="form-outline mb-4">
                    <input
                      v-model="fname"
                      type="text"
                      id="fname"
                      name="fname"
                      class="form-control form-control-lg"
                      placeholder="First Name"
                    />
                  </div>
  
                  <div class="form-outline mb-4">
                    <input
                      v-model="lname"
                      type="text"
                      id="lname"
                      name="lname"
                      class="form-control form-control-lg"
                      placeholder="Last Name"
                    />
                  </div>
  
                  <div class="form-outline mb-4">
                    <input
                      v-model="gender"
                      type="text"
                      id="gender"
                      name="gender"
                      class="form-control form-control-lg"
                      placeholder="Gender"
                    />
                  </div>
  
                  <div class="d-flex justify-content-center">
                    <button
                      type="submit"
                      class="btn btn-info btn-block btn-lg gradient-custom-4 text-body"
                    >
                      Update
                    </button>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        id: '', 
        fname: '',
        lname: '',
        gender: ''
      };
    },
    created() {
      this.fetchUserData(); 
    },
    methods: {
      fetchUserData() {
        const userId = this.$route.params.id; 
        axios.get(`http://localhost:2000/users/${userId}`)
          .then(response => {
            const userData = response.data;
            this.id = userData.id;
            this.fname = userData.first_name;
            this.lname = userData.last_name;
            this.gender = userData.gender;
          })
          .catch(error => {
            console.error('Failed to fetch user data:', error);
            // Handle the error
          });
      },
      updateUser() {
        const userData = {
          id: this.id,
          first_name: this.fname,
          last_name: this.lname,
          gender: this.gender
        };
  
        axios.put(`http://localhost:2000/users/${this.id}`, userData)
          .then(response => {
            console.log('User updated:', response.data);
            this.$router.push('/');
          })
          .catch(error => {
            console.error('Update failed:', error);
          });
      }
    }
  };
  </script>
  
  <style lang="scss" scoped>
  </style>
  