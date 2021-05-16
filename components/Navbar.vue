<template>
  <nav class="navbar is-light">
    <div class="container">
      <div class="navbar-brand p-2">
        <nuxt-link to="/">
         <img src="/logo.png" alt="logo" style="width: 250px;">
        </nuxt-link>
      </div>
      <div class="navbar-menu">
        <div class="navbar-end">
          <template v-if="$auth.loggedIn">
            <nuxt-link class="navbar-item" to="/dashboard">Dashboard</nuxt-link>
            <a class="navbar-item"  @click="logout">Logout</a>
          </template>
          <template v-else>
            <nuxt-link class="navbar-item" to="/register">Sign Up</nuxt-link>
            <nuxt-link class="navbar-item" to="/login">Sign In</nuxt-link>
          </template>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    async logout() {
      await this.$auth.logout();
      this.$router.push('/login')
    },
  }
}
</script>