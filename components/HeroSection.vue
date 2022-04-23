<template>
  <div class="w-100 hero-wrapper">
    <div class="hero-content">
      <h1 class="name">Dr. Iker Márquez Ambridge</h1>
      <p>Trabajamos para que no dejes de sonreír</p>
      <button>Pide tu cita</button>
    </div>
  </div>
</template>

<script>
export default {}
</script>
<style lang="postcss" scoped>
.hero-wrapper {
  background: url('/img/iker-background_big.png');
  background-position: top;
  background-size: contain;
  background-repeat: no-repeat;
  height: calc(80vh - var(--header-height) * 2);
  display: flex;
  justify-content: right;
  align-items: flex-start;
  text-align: center;
  margin-top: var(--header-height);
}
.hero-content {
  display: flex;
  flex-direction: column;
  justify-content: right;
  align-items: center;
  padding-right: 0.8rem;
  width: 65%;
}
.name {
  font-size: 2rem;
  color: #512882;
}
button {
  padding: 0.4rem 1rem;
  border: 2px solid #512882;
  border-radius: 0.8rem;
  background: #8e78b5;
  color: #fff;
  margin: 1rem;
  transition: all 0.2s ease;
  &:hover {
    background: #9e88c5;
    transition: all 0.2s ease;
  }
}

@screen md {
  .hero-wrapper {
    height: calc(100vh - var(--header-height-desktop));
    background-position: left;
    margin: 0 2rem;
    align-items: center;
    text-align: right;
  }
  .hero-content {
    padding-right: 2rem;
  }
}
</style>
