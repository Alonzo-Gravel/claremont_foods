

<template>
  <div class="container">
    <header class="header">
      <h1>Cape Town Food Fest 2025</h1>
      <p>
        Join us for a weekend of chefs, music, street vendors and unforgettable vibes.
        Explore our ticket tiers and find your perfect festival expe5rience.
      </p>
      <button class="theme-toggle" @click="toggleTheme">
        {{ isDark ? "Light Mode" : "Dark Mode" }} / 
        {{ isLight ? "Light Mode" : "Light Mode" }}
      </button>
    </header>

    <section class="ticket-section">
      <div style="margin-right:auto;">
        <label style="font-weight:700; color:var(--muted)"></label>
        <button class="filter-btn" @click="showAvailableOnly = !showAvailableOnly">
          {{ showAvailableOnly ? 'Show All' : 'Show Available Only' }}
        </button>
      </div>
      <div style="display:flex; gap:0.6rem;">
      <button class="btn-notify" @click="notifyMe">Notify Me</button>
      </div>
      <div class="ticket-grid">
        <TicketCard
          v-for="tier in ticketTiers"
          :key="tier.id"
          :name="tier.name"
          :price="tier.price"
          :benefits="tier.benefits"
          :featured="tier.featured"
          :isFavorited="tier.isFavorited"
          @toggle-favorite="toggleFavorite(tier.id)"
        />
      </div>
    </section>
  </div>
</template>

<script>

import TicketCard from "./components/TicketCard.vue";

export default {
  components: { TicketCard },

  data() {
    return {
      ticketTiers: [
        {
          id: 1,
          name: "Bronze Pass",
          price: 250,
          benefits: ["✅ General entry", "✅ Food stalls access", "🎶Live music"],
          featured: false,
          isFavorited: false,
        },
        {
          id: 2,
          name: "Silver Pass",
          price: 450,
          benefits: ["💥 All BRONZE perks", "✅VIP seating", "🍷🍷2 Free drinks"],
          featured: false,
          isFavorited: false
        },
        {
          id: 3,
          name: "Gold Pass",
          price: 600,
          benefits: ["💥 All SILVER perks", "🧑‍🍳 Meet the chefs", "✅ Backstage access"],
          featured: false,
          isFavorited: false
        }
      ]
    };
  },
  mounted() {
    // Load saved theme
    const savedTheme = localStorage.getItem("theme");

    if (savedTheme === "dark") {
      this.isDark = true;
      document.body.classList.add("dark-mode");
    }
  },
  methods: {
    toggleTheme() {
      this.isDark = !this.isDark;
      this.isLight = !this.isLight;

      if (this.isDark) {
        document.body.classList.add("dark-mode");
        localStorage.setItem("theme", "dark");
      } else {
        document.body.classList.remove("dark-mode");
        localStorage.setItem("theme", "light");
      }
   },

    toggleFavorite(id) {
      const tier = this.ticketTiers.find(t => t.id === id);
      tier.isFavorited = !tier.isFavorited;
    }
  }  
};

</script>


