<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">
          <img src="../assets/moodpix-logo.png" alt="Moodpix">
        </router-link>
        <button class="button navbar-burger" :class="{ 'is-active': mobile }"
        @click="toggleBurger">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
      <div class="navbar-menu" :class="{ 'is-active': mobile }">
        <div class="navbar-end">
          <router-link to="/signin" v-if="!isSignedIn" class="navbar-item">
            Sign In
          </router-link>
          <router-link to="/signup" v-if="!isSignedIn" class="navbar-item">
            Sign Up
          </router-link>
          <router-link to="/saved" v-if="isSignedIn" class="navbar-item">
            Saved
          </router-link>
          <a v-if="isSignedIn" class="navbar-item" @click="logout">Logout</a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'navbar',
  props: ['isSignedIn'],
  data() {
    return {
      mobile: false
    }
  },
  methods: {
    toggleBurger() {
      this.mobile = !this.mobile
    },
    logout() {
      this.toggleBurger()
      localStorage.removeItem('token')
      location.href = '/'
    }
  }
}
</script>

<style scoped>
  .navbar, .navbar-item:hover, .button.navbar-burger, .navbar-menu.is-active {
    background: rgba(255,255,255, 0.4) !important;
  }
</style>
