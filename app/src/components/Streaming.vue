<template>
  <section className="py-8 md:py-12 text-center relative overflow-hidden px-4">
    <h2 className="text-xl sm:text-2xl md:text-4xl font-gloria text-gray-900 mb-6 md:mb-12">
      <span class="text-orange-400">Unlock the Power of Music with Our</span>
      <br class="hidden sm:block" />
      Streaming API Services
    </h2>

    <div 
      ref="slideshowContainer"
      className="slideshow-container mt-4 md:mt-8 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 max-w-6xl mx-auto relative"
    >
      <!-- Card 1 -->
      <div 
        ref="card1"
        className="p-4 md:p-6 border-2 hover:border-green-500 rounded-lg shadow-md bg-white slideshow-card"
      >
        <div className="w-full h-32 md:h-40 flex items-center justify-center overflow-hidden">
          <img
            src="https://img.freepik.com/free-photo/dreamy-african-girl-listening-music-big-headphones-laughing-winsome-black-female-model-posing-with-longboard-pastel_197531-11151.jpg"
            alt="Music Streaming"
            className="w-full h-full object-cover rounded-md"
            loading="lazy"
          />
        </div>
        <h3 className="mt-3 md:mt-4 text-base md:text-lg font-semibold text-gray-900">
          Stream, Create, and Share Your Favorite Music Effortlessly
        </h3>
        <p className="mt-1 md:mt-2 text-xs md:text-sm text-gray-600">
          <span className="text-orange-600">
            Our Music Streaming API provides seamless access to a vast library of songs.
          </span>
        </p>
        <a
          href="#"
          className="mt-2 md:mt-3 inline-block text-xs md:text-sm font-semibold text-gray-800"
        >
          <span className="text-green-500">Explore</span> &rarr;
        </a>
      </div>

      <!-- Card 2 -->
      <div 
        ref="card2"
        className="p-4 md:p-6 border-2 hover:border-green-500 rounded-lg shadow-md bg-white slideshow-card"
      >
        <div className="w-full h-32 md:h-40 flex items-center justify-center overflow-hidden">
          <img
            src="https://img.freepik.com/free-photo/dreamy-african-girl-listening-music-big-headphones-laughing-winsome-black-female-model-posing-with-longboard-pastel_197531-11151.jpg"
            alt="Music Streaming"
            className="w-full h-full object-cover rounded-md"
            loading="lazy"
          />
        </div>
        <h3 className="mt-3 md:mt-4 text-base md:text-lg font-semibold text-gray-900">
          Build Custom Playlist and Discover New Artists with Ease
        </h3>
        <p className="mt-1 md:mt-2 text-xs md:text-sm text-gray-600">
          <span className="text-orange-600">
            Create personalized playlists and follow your favorite artists to enhance your music experience.
          </span>
        </p>
        <a
          href="#"
          className="mt-2 md:mt-3 inline-block text-xs md:text-sm font-semibold text-gray-800"
        >
          <span className="text-green-500">Create</span> &rarr;
        </a>
      </div>

      <!-- Card 3 -->
      <div 
        ref="card3"
        className="p-4 md:p-6 border-2 hover:border-green-500 rounded-lg shadow-md bg-white slideshow-card"
      >
        <div className="w-full h-32 md:h-40 flex items-center justify-center overflow-hidden">
          <img
            src="https://img.freepik.com/free-photo/dreamy-african-girl-listening-music-big-headphones-laughing-winsome-black-female-model-posing-with-longboard-pastel_197531-11151.jpg"
            alt="Music Streaming"
            className="w-full h-full object-cover rounded-md"
            loading="lazy"
          />
        </div>
        <h3 className="mt-3 md:mt-4 text-base md:text-lg font-semibold text-gray-900">
          Engage with a Community of Music Lovers and Share Your Passion
        </h3>
        <p className="mt-1 md:mt-2 text-xs md:text-sm text-gray-600">
          <span className="text-orange-600">
            Join a vibrant community where you can share your favorite songs, playlists, and artists.
          </span>
        </p>
        <a
          href="#"
          className="mt-2 md:mt-3 inline-block text-xs md:text-sm font-semibold text-gray-800"
        >
          <span className="text-green-500">Join</span> &rarr;
        </a>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

export default {
  setup() {
    const slideshowContainer = ref(null);
    const card1 = ref(null);
    const card2 = ref(null);
    const card3 = ref(null);

    onMounted(() => {
 
      if (window.innerWidth > 768) {
        gsap.registerPlugin(ScrollTrigger);

        // Set initial positions
        gsap.set([card1.value, card2.value, card3.value], {
          y: 100,
          opacity: 0,
          rotationX: 15
        });

        // Create continuous animation timeline
        const tl = gsap.timeline({
          scrollTrigger: {
            trigger: slideshowContainer.value,
            start: "top 80%",
            end: "bottom 20%",
            scrub: 1,
            markers: false
          }
        });

        tl.to(card1.value, {
          y: 0,
          opacity: 1,
          rotationX: 0,
          duration: 0.8,
          ease: "power3.out"
        })
        .to(card2.value, {
          y: 0,
          opacity: 1,
          rotationX: 0,
          duration: 0.8,
          ease: "power3.out"
        }, "-=0.5")
        .to(card3.value, {
          y: 0,
          opacity: 1,
          rotationX: 0,
          duration: 0.8,
          ease: "power3.out"
        }, "-=0.5")
        .to([card1.value, card2.value, card3.value], {
          y: -20,
          scale: 1.02,
          duration: 1,
          ease: "none"
        })
        .to([card1.value, card2.value, card3.value], {
          y: 0,
          scale: 1,
          duration: 1,
          ease: "none"
        });

        ScrollTrigger.create({
          trigger: slideshowContainer.value,
          start: "top center",
          end: "bottom center",
          onUpdate: (self) => {
            const progress = self.progress;
            const cards = [card1.value, card2.value, card3.value];
            
            cards.forEach((card, index) => {
              const offset = index * 0.1;
              const cardProgress = Math.max(0, Math.min(1, (progress - offset) * 1.5));
              
              if (card) {
                gsap.to(card, {
                  y: -10 * cardProgress,
                  scale: 1 + 0.05 * cardProgress,
                  boxShadow: `0 ${5 * cardProgress}px ${15 * cardProgress}px rgba(0,0,0,${0.1 * cardProgress})`,
                  duration: 0.3
                });
              }
            });
          }
        });
      } else {
        gsap.set([card1.value, card2.value, card3.value], { opacity: 0 });
        gsap.to([card1.value, card2.value, card3.value], {
          opacity: 1,
          duration: 0.5,
          stagger: 0.1,
          ease: "power1.out"
        });
      }
    });

    return {
      slideshowContainer,
      card1,
      card2,
      card3
    };
  }
};
</script>

<style scoped>
.slideshow-container {
  perspective: 1000px;
}

.slideshow-card {
  transform-style: preserve-3d;
  will-change: transform, opacity;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.slideshow-card:hover {
  transform: translateY(-5px) scale(1.03);
  box-shadow: 0 10px 20px rgba(0,0,0,0.15);
}

/* Mobile-specific adjustments */
@media (max-width: 640px) {
  .slideshow-container {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin: 0 auto;
  }
  
  .slideshow-card {
    margin-bottom: 1rem;
  }
}

/* Tablet adjustments */
@media (min-width: 641px) and (max-width: 1023px) {
  .slideshow-container {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>