<template>
	<section class="container">
		<img src="~assets/img/logo.png" alt="Nuxt.js Logo" class="logo">
		<h1 class="title">test autocomplete
      {{ ready }}
      <no-ssr>
			<vue-google-autocomplete
				v-if="ready"
				id="map"
				class="form-control"
				placeholder="Start typing"
				v-on:placechanged="getAddressData"
			></vue-google-autocomplete>
      </no-ssr>
		</h1>
		<ul class="users">
			<li v-for="(user, index) in users" :key="index" class="user">
				<nuxt-link :to="{ name: 'id', params: { id: index }}">{{ user.name }}</nuxt-link>
			</li>
		</ul>
	</section>
</template>

<script>
import axios from '~/plugins/axios'

export default {
  async asyncData () {
    return axios.get('/api/users').then((data) => {
      return { users: data, ready: true }
    }).catch((err) => {
      console.log(err)
    })
  },
  head () {
    return {
      title: 'Users'
    }
  },
  data () {
    return {
      ready: false
    }
  },
  methods: {
    getAddressData: function (addressData, placeResultData, id) {
      console.log(addressData)
      console.log(placeResultData)
      console.log(id)
    }
  }
}
</script>

<style scoped>
.title {
	margin: 30px 0;
}
.users {
	list-style: none;
	margin: 0;
	padding: 0;
}
.user {
	margin: 10px 0;
}
</style>
