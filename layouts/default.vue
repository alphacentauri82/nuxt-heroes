<template>
  <div>
    <header class="Header">
      <nuxt-link to="/">
        Home
      </nuxt-link>
      <nuxt-link to="/"><img src="https://res.cloudinary.com/wikeo/image/upload/c_scale,h_24/v1524136791/logo.svg" alt="Logo"></nuxt-link>
      <a v-if="connected" href="#" @click.prevent="logout">
        Logout
      </a>
      <a v-else :href="oauthUrl">
        Login
      </a>
    </header>
    <nuxt/>
    <footer class="Footer">
      Credits:
      <a href="https://www.instagram.com/aniketjatav/" target="_blank" rel="noopener">Images</a>
    </footer>
    <footer class="Footer">
      <a href="https://github.com/Atinux/nuxt-heroes" target="_blank" rel="noopener">Source code</a>
    </footer>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters(['oauthUrl']),
    ...mapGetters('auth', ['connected'])
  },
  methods: {
    async logout() {
      await this.$store.dispatch('auth/logout')
      this.$router.push('/')
    }
  }
}
</script>

<style lang="scss">
html
{
  font-family: "Impact", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 18px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: #000;
}
*, *:before, *:after
{
  box-sizing: border-box;
  margin: 0;
}
.Header {
  display: flex;
  padding: 20px;
  justify-content: space-between;
  border-bottom: 1px solid #333;
  a {
    color: #aaa;
    font-size: 18px;
    height: 24px;
    text-decoration: none;
    &:hover {
      color: #fff;
    }
  }
  img {
    height: 24px;
  }
}
.Footer {
  display: flex;
  padding: 20px;
  color: #fff;
  font-size: 16px;
  justify-content: center;
  border-top: 1px solid #333;
  a {
    text-decoration: none;
    color: #aaa;
    margin-left: 5px;
    &:hover {
      color: #fff;
    }
  }
}
.Title {
  text-align: center;
  text-transform: uppercase;
  padding: 40px 20px;
  color: #fff;
  font-size: 48px;
}
</style>
