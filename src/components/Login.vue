<template>
  <img src="../assets/logo.png" alt="logo" />
  <h1>Login</h1>
  <div class="login">
    <input type="email" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />

    <button @click="login" type="submit">Login</button>
    <p>
      <router-link to="/signup">Sign Up</router-link>
    </p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Login',
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async login() {
      let result = await axios.get(
        `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      )

      if (result.status === 200 && result.data.length > 0) {
        localStorage.setItem('user-info', JSON.stringify(result.data[0]))
        this.$router.push({ name: 'Home' })
      }

      console.log(result)
    },
  },
  mounted() {
    let user = localStorage.getItem('user-info')

    if (user) {
      this.$router.push({ name: 'Home' })
    }
  },
}
</script>
