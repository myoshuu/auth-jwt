<template>
  <form action="" @submit.prevent="login">
    Email :
    <input type="email" name="email" id="email"> <br>
    Password :
    <input type="password" name="password" id="password">
    <button>Login</button>
  </form>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
        // 
      }
  },
  methods: {
    login(e) {
      const data = new FormData(e.currentTarget);
      const values = Object.fromEntries(data.entries());

      console.log(values);
    
      axios.post('http://localhost:8000/api/auth/login', values)
        .then(res => {
        localStorage.setItem('token', res.data.token)
      })
      .catch(err => {
        console.log(err); 
      })
    }
  }
}
</script>