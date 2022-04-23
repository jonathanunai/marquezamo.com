<template>
  <main>
    <hero-section />
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <p>
        Esta página está en construcción y en muy poco tiempo podremos ofrecer nuestros servicios aquí mismo. De
        mientras pueden ponerse en contacto con nostotros aquí:
      </p>
      <h2 class="subtitle text-center">{{ site[this.$i18n.locale].sitename }}</h2>
      <img :src="logoUrl" alt="" class="site-logo" />
      <ul>
        <li>{{ site[this.$i18n.locale].siteemail }}</li>
        <li>{{ site[this.$i18n.locale].sitephone }}</li>
        <li>{{ site[this.$i18n.locale].siteaddress }}</li>
      </ul>
      <p>Gracias por la comprensión, ¡nos vemos en breve!</p>
    </section>
  </main>
</template>
<script>
export default {
  name: 'index',
  async asyncData({ $content, error }) {
    let site
    try {
      site = await $content('site').fetch()
    } catch (e) {
      error({ message: 'Site data not found' })
    }
    site = site[0]
    return { site }
  },
  head() {
    return {
      title: this.site[this.$i18n.locale].sitename,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: this.site[this.$i18n.locale].sitedescription,
        },
      ],
    }
  },
  computed: {
    logoUrl() {
      return this.$colorMode.value === 'light' ? '/img/icon.png' : '/img/icon_dark.png'
    },
  },
}
</script>
<style scoped>
main {
  padding: 0 1rem;
}
ul {
  margin: 2rem;
  color: #512882;
}
li {
  margin-bottom: 0.3rem;
  text-align: center;
}
p {
  font-size: 1.2rem;
  text-align: center;
}
.site-logo {
  max-width: 140px;
  margin: 1rem;
}
</style>
