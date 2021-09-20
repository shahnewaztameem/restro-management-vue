<template>
  <Header />
  <h1>Add restaurant page</h1>

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
      Add a new restaurant
    </button>
  </form>
</template>

<script>
import Header from './Header'
import axios from 'axios'

export default {
  name: 'Add',
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

  methods: {
    async addRestaurant() {
      const result = await axios.post('http://localhost:3000/restaurant', {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact,
      })

      if (result.status === 201) {
        this.$router.push({ name: 'Home' })
      }

      
    },
  },
  mounted() {
    let user = localStorage.getItem('user-info')

    if (!user) {
      this.$router.push({ name: 'SignUp' })
    }
  },
}
</script>
