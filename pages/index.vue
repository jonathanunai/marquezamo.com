<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <img src="/img/icon.png" alt="" />
      <h2 class="subtitle text-center">{{ site[this.$i18n.locale].sitename }}</h2>
      <ul>
        <li>{{ site[this.$i18n.locale].siteemail }}</li>
        <li>{{ site[this.$i18n.locale].sitephone }}</li>
        <li>{{ site[this.$i18n.locale].siteaddresss }}</li>
      </ul>
    </section>
  </main>
</template>
<script>
export default {
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
}
</script>
<style>
ul {
  margin-top: 1rem;
}
li {
  margin-bottom: 0.3rem;
}
</style>
