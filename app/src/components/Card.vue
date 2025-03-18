<template>
  <div class="bg-white text-orange-600 max-w-screen-xl mx-auto p-8">
    <h1 class="text-4xl font-gloria mb-6 text-center">🎵 Music Library</h1>
    <div v-if="songs.length" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10 px-4">
      <div
        v-for="(song, index) in songs"
        :key="song.id"
        :ref="el => cardRefs[index] = el"
        class="bg-yellow-500 hover:bg-orange-600 p-6 rounded-xl shadow-lg transition duration-300 flex flex-col items-start opacity-0"
      > 
        <h2 class="text-lg text-black font-semibold">{{ song.title }}</h2>
        <p class="text-sm text-black">by {{ song.artist.name }}</p>
        <a :href="song.youtube_url" target="_blank" class="mt-3 inline-block border-2 border-orange-600 bg-yellow-500 text-white px-4 py-2 rounded-md text-sm">🎧 Listen</a>
      </div>
    </div>
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
    };
  },
  async created() {
    try {
      const response = await fetch("http://127.0.0.1:8000/api/music/songs/");
      this.songs = await response.json();
    } catch (error) {
      console.error("Error fetching songs:", error);
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
