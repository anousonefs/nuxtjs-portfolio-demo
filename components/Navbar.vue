<template>
  <div>
  <b-navbar type="dark" variant="dark">
    <b-navbar-nav>
      <b-nav-item href="/">
      <NuxtLogo class="logo"/>
      </b-nav-item>
      <b-nav-item href="/">Home</b-nav-item>
      <b-nav-item href="/blog">Blog</b-nav-item>
      <b-nav-item href="/photos">Photos</b-nav-item>
      <b-nav-item href="/about">About</b-nav-item>

      <!-- Navbar dropdowns -->
      <b-nav-item-dropdown text="Lang" right>
        <b-dropdown-item href="#">EN</b-dropdown-item>
        <b-dropdown-item href="#">ES</b-dropdown-item>
        <b-dropdown-item href="#">RU</b-dropdown-item>
        <b-dropdown-item href="#">FA</b-dropdown-item>
      </b-nav-item-dropdown>

      <b-nav-item-dropdown text="User" right>
        <b-dropdown-item href="/profile">Profile</b-dropdown-item>
        <b-dropdown-item href="#">Settings</b-dropdown-item>
      </b-nav-item-dropdown>
      <b-button v-if="loggedIn" @click="logOut">LogOut</b-button>
      <b-nav-item v-else href="/login" class="btn btn-success mr-5" right>Login</b-nav-item>
    </b-navbar-nav>
  </b-navbar>
</div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  computed: {
    ...mapState('auth', ['loggedIn'])
  },
  methods: {
    async logOut(){
      await this.$auth.logout()
      this.$router.push('/')
    }
  },
}
</script>

<style scoped>
  .logo{
    width: 32px;
    height: 32px;
  }
</style>