<template>
  <main class="self-center flex flex-col items-center justify-center">
    <section class="self-center flex flex-col items-center justify-center">
      <h2 class="title text-center">{{ site[this.$i18n.locale].sitename }}</h2>
      <h5 class="text-center pb-4">{{ site[this.$i18n.locale].sitedescription }}</h5>
      <img :src="logoUrl" alt="" class="site-logo" />
      <ul>
        <li>{{ site[this.$i18n.locale].siteemail }}</li>
        <li>{{ site[this.$i18n.locale].sitephone }}</li>
        <li>{{ site[this.$i18n.locale].siteaddress }}</li>
      </ul>
      <p>
        {{ site[this.$i18n.locale].construction }}
      </p>
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
      return '/img/icon.png'
    },
  },
}
</script>
<style scoped>
main {
  padding: 0 1rem;
  height: calc(100vh - var(--header-height));
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
  text-align: center;
}
.site-logo {
  max-width: 140px;
  margin: 1rem;
}
h5 {
  font-size: 1.2rem;
}
</style>
