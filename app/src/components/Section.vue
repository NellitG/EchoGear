<template>
  <section
    class="min-h-screen bg-gray-100 flex items-center justify-center"
  >
    <div class="max-w-4xl mx-auto flex flex-col gap-6">
      <!-- Heading & Description in Two Columns -->
      <div class="flex flex-col md:flex-row justify-between items-start">
        <!-- Left: Heading -->
        <h1
          class="text-4xl md:text-5xl mb-24 font-gloria text-gray-900 leading-tight md:w-1/2"
        >
         <span class="text-orange-600"> Unleash Your Music</span> <br />
          with Our Streaming<br />
          API
        </h1>

        <!-- Right: Description + Buttons -->
        <div class="md:w-1/2">
          <p class="text-gray-950 text-lg font-gloria">
            Discover, stream, and share your favorite tunes effortlessly. Join
            our community and elevate your music experience today!
          </p>
          <!-- Buttons Below the Paragraph -->
          <div class="flex gap-4 mt-4">
            <a
              href="#"
              class="border-green-400 bg-green-400 text-white text-black px-6 py-3 font-semibold rounded-lg shadow-md transition"
            >
              Get Started
            </a>
            <a
              href="#"
              class="border px-6 py-3 font-semibold rounded-lg text-gray-900 hover:bg-orange-600 transition"
            >
              Learn More
            </a>
          </div>
        </div>
      </div>

      <!-- Image (Below All Text) -->
      <div>
        <img
          src="../assets/ladies.avif"
          alt="Music Streaming"
          class="mb-24 justify-self-center w-full rounded-lg "
        />
      </div>
    </div>
  </section>
</template>
