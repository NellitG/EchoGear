<template>
  <div class="bg-white text-orange-600 max-w-screen-xl mx-auto p-8">
    <h1 class="text-4xl font-gloria mb-6 text-center">🎵 Music Library</h1>
    <div v-if="songs.length" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10 w-full px-4">
      <div
        v-for="(song, index) in songs"
        :key="song.id"
        :ref="el => cardRefs[index] = el"
        class="hover:bg-orange-400 bg-green-50 p-6 rounded-xl shadow-lg transition duration-300 flex flex-col items-start opacity-0"
      > 
        <h2 class="text-lg text-black font-semibold">{{ song.title }}</h2>
        <p class="text-sm text-black">by {{ song.artist_name || song.artist?.name }}</p>
        <a 
          v-if="song.youtube_url" 
          :href="song.youtube_url" 
          target="_blank" 
          class="mt-3 inline-block border-2 bg-orange-400 text-white px-4 py-2 rounded-md text-sm"
        >
          🎧 Listen
        </a>
      </div>
    </div>
    <div v-else-if="loading" class="text-center text-gray-400">Loading songs...</div>
    <p v-else class="text-center text-gray-400">No songs available.</p>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  data() {
    return {
      songs: [],
      cardRefs: [],
      loading: true,
      error: null
    };
  },
  async created() {
    try {
      const response = await fetch("http://127.0.0.1:8000/api/music/songs/", {
        headers: {
          'Accept': 'application/json',
          'Content-Type': 'application/json'
        }
      });
      
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      
      const data = await response.json();
      this.songs = data.results || data; // Handle both list and paginated responses
    } catch (error) {
      console.error("Error fetching songs:", error);
      this.error = "Failed to load songs. Please try again later.";
    } finally {
      this.loading = false;
    }
  },
  updated() {
    this.$nextTick(() => {
      this.animateCards();
    });
  },
  methods: {
    animateCards() {
      if (this.cardRefs.length === 0) return;

      gsap.fromTo(
        this.cardRefs,
        { opacity: 0, y: 50 },
        {
          opacity: 1,
          y: 0,
          duration: 1,
          stagger: 0.2,
          ease: "power2.out",
          scrollTrigger: {
            trigger: this.$el,
            start: "top 80%",
          },
        }
      );
    },
  },
};
</script>