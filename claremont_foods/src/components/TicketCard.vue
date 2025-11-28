

<template>
  <div class="ticket-card" :class="{ featured: featured }">

    <h2 class="tier-name">{{ name }}</h2>
    <p class="tier-price">R{{ price }}</p>

    <ul class="benefits">
      <li v-for="(b, i) in benefits" :key="i">{{ b }}</li>
    </ul>

    <button 
      class="fav-btn" 
      :class="{ active: isFavorited }"
      @click="$emit('toggle-favorite')"
    >
      {{ isFavorited ? "★ Favorited" : "☆ Favourite" }}
    </button>

  </div>
</template>

<script>
export default {
  props: {
    name: String,
    price: Number,
    benefits: Array,
    featured: Boolean,
    isFavorited: Boolean,

  }
};
</script>