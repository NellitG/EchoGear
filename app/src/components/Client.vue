<template>
    <div class="bg-green-50 min-h-screen-xl mx-auto p-8 text-center">
      <h2 class="text-3xl font-gloria text-orange-600 mb-6">🎶 Our Sponsors</h2>
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-6 items-center">
        <div v-for="sponsor in sponsors" :key="sponsor.name" class="flex flex-col items-center space-y-2 font-gloria">
          <img :src="sponsor.logo" :alt="sponsor.name" class="w-16 h-16 object-contain hover:scale-110 transition duration-300">
          <p class="text-gray-800 font-medium">{{ sponsor.name }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        sponsors: [
          { name: "YouTube", logo: "https://upload.wikimedia.org/wikipedia/commons/b/b8/YouTube_Logo_2017.svg" },
          { name: "Spotify", logo: "https://upload.wikimedia.org/wikipedia/commons/8/84/Spotify_icon.svg" },
          { name: "Boomplay", logo: "https://www.boomplay.com/pc/img/download/app_logo1.png" }, 
          { name: "BandLab", logo: "data:image/png;base64,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" }, 
          { name: "Apple Music", logo: "https://upload.wikimedia.org/wikipedia/commons/2/2a/Apple_Music_logo.svg" },
          { name: "Shazam", logo: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSZAENtH3SFoBESrGR_8qA7Mi5nR4E5RDdIaQ&s" }
        ],
      };
    },
  };
  </script>
  