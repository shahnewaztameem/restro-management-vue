<template>
  <Header />
  <h1>Add restaurant page</h1>
</template>

<script>
import Header from './Header'

export default {
  name: 'Add',
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
