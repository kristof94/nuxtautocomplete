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
	</section>
</template>

<script>

export default {
  mounted () {
    const _this = this
    _this.ready = true
    /*
    var promise1 = Promise.resolve(123)

    promise1.then(function (value) {
      console.log(value)
      _this.ready = true
    }) */
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
