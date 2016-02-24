<template>
  <div class="">
    <input type="text" v-model="username" placeholder="edit me">
    <button v-on:click="getGithubInfo" type="button" name="button">get user</button>
    <p>
    <img v-bind:src="user.avatar_url"/>
    <h2>{{user.name}}</h2>
    {{user.location}}
    </p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      user: {}
    }
  },
  ready: function () {
    this.getGithubInfo()
  },
  methods: {
    getGithubInfo: function () {
      this.$http({url: 'https://api.github.com/users/' + this.$get('username'), method: 'GET'})
      .then(function (response) {
        this.$set('user', response.data)
        console.log(response.data)
      }, function (response) {

      })
    }
  }
}
</script>

<style media="screen" scoped>

  p {
    color:red;
  }
  
</style>
