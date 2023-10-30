<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link v-bind:to="{ name: 'about' }">About</router-link> |
    <router-link v-bind:to="{ name: 'Jobs' }">Jobs</router-link>
  </nav>

  <button @click="redirect">redirect</button>
  <button @click="back">back</button>
  <button @click="forward">forward</button>

  <router-view/>
</template>

<script>

export default {
  methods: {
    redirect() { this.$router.push({ name: 'home' }) },
    back() { this.$router.go(-1) },
    forward() { this.$router.go(1) }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  color: white;
  border-radius: 10px;
  background: #7cb5ed;
  padding: 5px;
  font-weight: bold;
  text-decoration: none;
  margin: 0 5px;
}

nav a.router-link-exact-active {
  color: white;
  border: 0;
  border-radius: 10px;
  border-bottom: 1.5px solid red;
  background: #7cb5ed;
  padding: 5px;
  font-weight: bold;
}
button {
  margin: 0 10px;
  padding: 10px;
  border: none;
  border-radius: 4px;
}
</style>
