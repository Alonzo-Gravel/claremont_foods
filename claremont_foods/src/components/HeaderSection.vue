<template>
  <header class="hero">
    <div class="container hero-inner">
      <div>
        <h1 class="event-title">Cape Town Food Fest</h1>
        <p class="event-sub">A weekend of food, music & community — explore ticket options below.</p>
      </div>

      <div class="fav-box" aria-live="polite">
        <div class="fav-label">Favourites</div>
        <div :class="['fav-count', { bump: animate }]" ref="countEl">{{ count }}</div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderSection',
  props: {
    count: { type: Number, required: true },
    animate: { type: Boolean, default: false }
  }
};
</script>

<style scoped>
/* header-specific styles are in global style.css; keep this small */
</style>