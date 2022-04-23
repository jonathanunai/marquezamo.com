<template>
  <nav class="nav fixed z-40 top-0 inset-x-0 p-1" aria-label="Main Menu">
    <ul class="flex">
      <li class="flex ml-2"><img src="/img/small-logo.png" alt="" class="h-10" /></li>
      <li class="flex-1 ml-2 flex flex-row"><span>CLÍNICA DENTAL</span><span>Márquez-Amo</span></li>
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
}
.scrim-bg-none {
  &::before {
    content: '';
    z-index: -1;
    background-color: #fff;
    @apply absolute top-0 inset-x-0 h-12 transition-all duration-500 ease-in-out;
  }
  &::after {
    content: '';
    z-index: -1;
    opacity: 1;
    animation: fadeIn1 500ms ease-in-out;
    margin-bottom: -4rem;
    @apply pointer-events-none absolute bottom-0 inset-x-0 h-16 transition-all duration-500 ease-in-out;
    background: linear-gradient(to bottom, #111827, cubic-bezier(0.15, 0, 0.45, 1), transparent);
  }
  img {
    position: absolute;
    padding-top: 4rem;
    padding-left: 2rem;
    height: auto;
  }
}
.nuxt-link-exact-active {
  @apply text-gray-200 border-gray-400 bg-gray-800 bg-opacity-25 cursor-default;
}

.light {
  & .scrim-bg-none {
    &::after {
      animation-name: fadeIn2;
      background: linear-gradient(to bottom, #e5e7eb, cubic-bezier(0.15, 0, 0.45, 1), transparent);
    }
  }
  & .nuxt-link-exact-active {
    @apply text-primary-700 border-gray-600 bg-gray-100;
  }
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
