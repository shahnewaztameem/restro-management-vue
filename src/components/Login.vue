<template>
  <img src="../assets/logo.png" alt="logo" />
  <h1>Login</h1>
  <div class="login">
   
    <input type="email" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />

    <button type="submit">Login</button>
    <p>
      <router-link to="/signup">Sign Up</router-link>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Login',
}
</script>
