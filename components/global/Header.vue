<template>
  <nav class="scrim-bg fixed z-40 top-0 inset-x-0 pt-3 px-3" aria-label="Main Menu">
    <ul class="flex">
      <li class="flex-1">
        <nuxt-link class="btn block" to="/">Home</nuxt-link>
      </li>
      <li class="flex-1 ml-2">
        <nuxt-link class="btn block" to="/blog">Blog</nuxt-link>
      </li>
      <li class="flex-1 ml-2">
        <nuxt-link class="btn block" to="/projects">Projects</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="postcss" scoped>
.div {
  display: block;
  position: relative;
  top: -2px;
  height: 50px;
  background-image: url('data:image/svg+xml;utf8,<svg viewBox="0 0 1440 50" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path fill="rgba(58, 0, 174, 1)" d="M 0 50 C 357 50 357 424 714 424 L 714 424 L 714 0 L 0 0 Z" stroke-width="0"></path> <path fill="rgba(58, 0, 174, 1)" d="M 713 424 C 1076.5 424 1076.5 50 1440 50 L 1440 50 L 1440 0 L 713 0 Z" stroke-width="0"></path> </svg>');
  background-size: cover;
  background-repeat: no-repeat;
}

@media (max-width: 1439px) {
  .div {
    background-size: contain;
  }
}

.scrim-bg {
  &::before {
    content: '';
    z-index: -1;
    background-color: var(--bg);
    @apply absolute bottom-0 inset-x-0 h-12 mb-4 transition-colors duration-200 ease-in-out;
  }
  &::after {
    content: '';
    z-index: -1;
    opacity: 1;
    animation: fadeIn1 500ms ease-in-out;
    margin-bottom: -4.75rem;
    @apply pointer-events-none absolute bottom-0 inset-x-0 h-16;
    background: linear-gradient(to bottom, #111827, cubic-bezier(0.15, 0, 0.45, 1), transparent);
  }
}
.nuxt-link-exact-active {
  @apply text-gray-200 border-gray-400 bg-gray-800 bg-opacity-25 cursor-default;
}

.light {
  & .scrim-bg {
    &::after {
      animation-name: fadeIn2;
      background: linear-gradient(to bottom, #e5e7eb, cubic-bezier(0.15, 0, 0.45, 1), transparent);
    }
  }
  & .nuxt-link-exact-active {
    @apply text-primary-700 border-gray-600 bg-gray-100;
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
