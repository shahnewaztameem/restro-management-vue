<template>
  <Header />
  <h1>Update restaurant page</h1>
</template>

<script>
import Header from './Header'

export default {
  name: 'Update',
  components: {
    Header,
  },
  mounted() {
    let user = localStorage.getItem('user-info')

    if (!user) {
      this.$router.push({ name: 'SignUp' })
    }
  },
}
</script>
