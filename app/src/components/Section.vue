<template>
  <section class="min-h-screen bg-gray-100 flex items-center justify-center p-4">
    <div class="max-w-4xl mx-auto flex flex-col gap-6">
      <div class="flex flex-col sm:flex-col md:flex-row justify-between items-center md:items-start text-center md:text-left">
        <!-- Left: Heading -->
        <h1 class="text-3xl md:text-5xl font-gloria text-gray-900 leading-tight md:w-1/2">
          <span class="text-orange-600">Unleash Your Music</span><br />
          with Our Streaming<br />
          API
        </h1>

        <!-- Right: Description + Buttons -->
        <div class="md:w-1/2">
          <p class="text-gray-950 text-lg font-gloria mt-4 md:mt-0">
            Discover, stream, and share your favorite tunes effortlessly. Join our community and elevate your music experience today!
          </p>
          <!-- Buttons Below the Paragraph -->
          <div class="flex flex-wrap justify-center md:justify-start gap-4 mt-6">
            <a
              href="#"
              class="bg-green-400 text-white px-6 py-3 font-semibold rounded-lg shadow-md transition hover:bg-green-500"
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
          class="w-full rounded-lg"
        />
      </div>
    </div>
  </section>
</template>
