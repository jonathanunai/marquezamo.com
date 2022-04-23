<template>
  <div class="wrapper">
    <Header />
    <nuxt />
  </div>
</template>
<script>
export default {
  methods: {
    handleSCroll() {
      if (process.browser) {
        const body = document.body
        if (window.scrollY > 100 && !body.className.includes('scrolled')) {
          body.classList.add('scrolled')
        } else if (window.scrollY < 100) {
          body.classList.remove('scrolled')
        }
      }
    },
  },
  created() {
    if (process.browser) {
      window.addEventListener('scroll', this.handleSCroll)
    }
  },
  destroyed() {
    if (process.browser) {
      window.removeEventListener('scroll', this.handleSCroll)
    }
  },
}
</script>
