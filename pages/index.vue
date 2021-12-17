<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <img src="/img/logo-marquez-amo.jpg" alt="" />
      <h2 class="subtitle text-center">{{ site.sitename }}</h2>
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
}
</script>
