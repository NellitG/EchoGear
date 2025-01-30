<template>
    <section class="bg-white">
      <div
        class="grid max-w-screen-xl px-4 py-8 mx-auto lg:gap-8 xl:gap-0 lg:py-16 lg:grid-cols-12"
      >
        <div class="mr-auto place-self-center lg:col-span-7">
          <h1
            class="max-w-2xl mt-4 mb-4 text-4xl font-gloria tracking-tight leading-none md:text-5xl xl:text-6xl"
            style="font-family: 'Gloria Hallelujah', serif"
           >
            Payments tool for<br><span class="text-orange-600"> software companies</span>
          </h1>
          <p
            class="max-w-2xl mb-6 font-light text-gray-500 lg:mb-8 md:text-lg lg:text-xl"
          >
            From checkout to global sales tax compliance, companies around the world
            use Flowbite to simplify their payment stack.
          </p>
          <a
            href="#"
            class="inline-flex items-center justify-center px-5 py-3 mr-3 text-base font-medium text-center text-black rounded-lg bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300"
          >
            Get started
            <svg
              class="w-5 h-5 ml-2 -mr-1"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </a>
          <a
            href="#"
            class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border border-gray-300 rounded-lg hover:bg-gray-100 focus:ring-4 focus:ring-gray-100"
          >
            Speak to Sales
          </a>
        </div>
        <div class="lg:mt-0 lg:col-span-5 lg:flex">
          <img
            ref="headphonesImage"
            src="https://img.freepik.com/premium-photo/photo-headphones_931878-314997.jpg?ga=GA1.1.487577296.1727511220&semt=ais_hybrid"
            alt="mockup"
          />
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { gsap } from "gsap";
  
  export default {
    name: "HeroSection",
    mounted() {
      // Rotate the image continuously
      gsap.to(this.$refs.headphonesImage, {
        rotationY: 360, 
        duration: 5, 
        repeat: -1, 
        ease: "linear",
      });
    },
  };
  </script>