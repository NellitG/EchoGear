<template>
    <div className="flex flex-col items-center justify-center p-8 bg-green-50 border-gray-300">
    
      <div className="flex space-x-1 text-black">
            <span key={index} className="text-xl">★★★★★</span>
      </div>

   
      <p className="mt-4 text-center text-lg font-semibold text-black">
        "Using this API has transformed how we engage with music. It’s<br> intuitive and has opened up endless possibilities for our platform!"
      </p>
      <div className="flex items-center mt-4 space-x-3">
        <div className="w-10 h-10 bg-gray-300 rounded-full flex items-center justify-center">
          <span className="text-gray-500 text-sm font-bold">🚀</span>
        </div>
        <div>
          <p className="text-sm font-semibold text-gray-700">Nelson Chiuri</p>
          <p className="text-xs text-gray-500">CEO, MusicHub</p>
        </div>
      </div>
    </div>
</template>
<script>
export default {
  name: 'Testimonial',
  props: {
    index: {
      type: Number,
      required: true
    }
  }
}
</script>