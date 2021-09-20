<template>
  <Header />
  <h1>Update restaurant page</h1>
  <form class="add">
    <input
      type="text"
      name="name"
      placeholder="Enter Name"
      v-model="restaurant.name"
    />
    <input
      type="text"
      name="address"
      placeholder="Enter Address"
      v-model="restaurant.address"
    />
    <input
      type="text"
      name="contact"
      placeholder="Enter Contact"
      v-model="restaurant.contact"
    />
    <button type="button" @click="addRestaurant">
      Update restaurant
    </button>
  </form>
</template>

<script>
import Header from './Header'
import axios from 'axios'

export default {
  name: 'Update',
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: '',
        address: '',
        contact: '',
      },
    }
  },
  async mounted() {
    let user = localStorage.getItem('user-info')

    if (!user) {
      this.$router.push({ name: 'SignUp' })
    }

    const result = await axios.get(
      `http://localhost:3000/restaurant/${this.$route.params.id}`
    )

    this.restaurant = result.data
  },
}
</script>
