<template>
  <div class="sign-up">
    <!--form-->
      <form  @submit="formSubmit" style="padding-top:40px" id="signupForm">
  <!-- text -->
  <p>
    <label>Email/Username</label>
    <input type="text" v-model="user.username">
  </p>
  <p>
    <label>Password</label>
    <input type="text" v-model="user.password">
  </p>
  <button type="submit">Register</button>
</form>

    <!--end here-->
  </div>
</template>

<script>
  import axios from 'axios'

export default {
  name: 'SignUp',
data() {
        return {  
          user: {"username":"samenda","password":"samenda"}
        }
      },
methods: {
    formSubmit(e) {
      console.log(this.user.username)
      axios.post('http://localhost:8082/signup', {
  name: this.user.username,
  company: this.user.password
})
        .then((resp) => {
          this.user=resp.data
          console.log(resp)
        })
        .catch((err) => {
          console.log(err)
        })
    }
}
}
</script>
<style scoped>

</style>