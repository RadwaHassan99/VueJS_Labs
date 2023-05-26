<template>
  <div class="mask d-flex align-items-center h-100 gradient-custom-3 mt-5 p-5">
    <div class="container h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-9 col-lg-7 col-xl-6">
          <div class="card" style="border-radius: 15px">
            <div class="card-body p-5">
              <h2 class="text-uppercase text-center mb-5">Add New User</h2>

              <form @submit.prevent="registerUser">

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
                    Register
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
      fname: '',
      lname: '',
      gender: ''
    };
  },

  methods: {
    registerUser() {
      const userData = {
        first_name: this.fname,
        last_name: this.lname,
        gender: this.gender
      };

      axios.post('http://localhost:2000/users', userData)
        .then(response => {
          console.log('User registered:', response.data);
          this.$router.push('/');
         
        })
        .catch(error => {
          console.error('Registration failed:', error);
        
        });
    }
  }
};
</script>

<style lang="scss" scoped>
</style>