<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <img :src="logoUrl" alt="" class="site-logo" />
      <h2 class="subtitle text-center">{{ site[this.$i18n.locale].sitename }}</h2>
      <ul>
        <li>{{ site[this.$i18n.locale].siteemail }}</li>
        <li>{{ site[this.$i18n.locale].sitephone }}</li>
        <li>{{ site[this.$i18n.locale].siteaddress }}</li>
      </ul>
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
<style>
ul {
  margin-top: 1rem;
}
li {
  margin-bottom: 0.3rem;
}
.site-logo {
  max-width: 60%;
  margin-bottom: 3rem;
}
</style>
