<template>
  <div class="bg-white text-orange-600 max-w-screen-xl mx-auto p-8">
    <h1 class="text-4xl font-semibold mb-6 text-center">🎵 Music Library</h1>
    <div v-if="songs.length" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10 px-4">
      <div v-for="song in songs" :key="song.id" class="bg-yellow-500 hover:bg-orange-600 p-6 rounded-xl shadow-lg transition duration-300 flex flex-col items-start"> 
        <h2 class="text-lg text-black font-semibold">{{ song.title }}</h2>
        <p class="text-sm text-gray-950">by {{ song.artist.name }}</p>
        <a :href="song.youtube_url" target="_blank" class="mt-3 inline-block border-2 border-orange-600 bg-yellow-500 text-white px-4 py-2 rounded-md text-sm">🎧 Listen</a>
      </div>
    </div>
    <p v-else class="text-center text-gray-400">No songs available.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      songs: [],
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
};
</script>
