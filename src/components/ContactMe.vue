<script setup>

</script>

<template>
  <section>
    <div class="flex items-center mb-8 w-full">
      <svg class="mr-3 mt-1" height="2" width="32">
        <line class="stroke-primary stroke-2" x1="0" y1="0" x2="32" y2="0" />
      </svg>
      <h4 class="text-white text-opacity-80 text-lg font-semibold">More Info.</h4>
    </div>
    <div>
      <h4 class="text-white text-opacity-80 text-lg font-semibold text-center mb-2">
        Get In Touch.
      </h4>
      <p class="text-white text-opacity-50 text-sm text-center leading-snug">
        I’m looking for any opportunities to help solving your problems,
        if you’re interested you can leave a message there and
        I’ll try my best to get it back to you. Also feel free to ask anything
        to me or just say hi by connect to my socials.
      </p>
    </div>
    <form class="mt-8" @submit.prevent="">
      <label for="your-name" class="text-white text-opacity-50 text-sm">Name</label>
      <input
        class="bg-transparent border border-white border-opacity-25 rounded-sm
          py-3 px-2 mb-2 text-white text-opacity-80 w-full text-sm"
        type="text"
        name="your-name"
        id="your-name"
      >
      <label for="your-email" class="text-white text-opacity-50 text-sm">Email Address</label>
      <input
        class="bg-transparent border border-white border-opacity-25 rounded-sm
          py-3 px-2 mb-2 text-white text-opacity-80 w-full text-sm"
        type="email"
        name="your-email"
        id="your-email"
      >
      <label for="your-message" class="text-white text-opacity-50 text-sm">Text Message</label>
      <textarea
        class="bg-transparent border border-white border-opacity-25 rounded-sm
          py-3 px-2 mb-2 text-white text-opacity-80 w-full text-sm"
        name="text-message"
        id="your-message"
        cols="30"
      ></textarea>
      <button
        class="py-3 px-6 border border-primary rounded-sm text-sm text-primary"
        type="submit"
      >
        Send message
      </button>
    </form>
  </section>
</template>
