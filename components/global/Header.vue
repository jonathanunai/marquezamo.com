<template>
  <nav class="nav fixed z-40 top-0 inset-x-0 p-1" aria-label="Main Menu">
    <ul class="flex">
      <li class="flex ml-2"><img src="/img/small-logo.png" alt="" class="h-10" /></li>
      <li class="flex ml-2 flex flex-row bold">CLÍNICA DENTAL Márquez-Amo</li>
      <li class="flex ml-2 text-right">
        <nuxt-link :to="switchLocalePath('en')"> [En] </nuxt-link>
        <nuxt-link :to="switchLocalePath('es')"> [Es] </nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      locale: { es: { msg: 'Página en construcción...' }, en: { msg: 'Comming soon...' } },
    }
  },
}
</script>

<style lang="postcss" scoped>
@media (max-width: 1439px) {
  .div {
    background-size: contain;
  }
}
ul {
  align-items: center;
  width: 100%;
  justify-content: space-between;
  margin: 0 auto;
}
nav {
  height: var(--header-height);
  align-items: center;
  display: flex;
  background: #ffffff;
  a {
    margin: 0 0.2rem;
  }
}

.nuxt-link-exact-active {
  @apply text-gray-200 bg-primary-400 bg-opacity-25 cursor-default;
}

@screen md {
  nav {
    height: var(--header-height-desktop);
  }
}

/* Need two because of smoother switching between color modes */
@keyframes fadeIn1 {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@keyframes fadeIn2 {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
