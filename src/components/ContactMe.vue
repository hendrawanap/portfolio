<script setup>

</script>

<template>
  <section>
    <div class="flex items-center mb-8 w-full">
      <svg class="mr-3 mt-1" height="2" width="32">
        <line class="stroke-primary stroke-2" x1="0" y1="0" x2="32" y2="0" />
      </svg>
      <h4 class="text-opacity-80">More Info.</h4>
    </div>
    <div class="flex flex-col md:flex-row md:pl-10">
      <div class="md:mr-10 md:w-1/2">
        <h4 class="text-opacity-80 text-center mb-2">
          Get In Touch.
        </h4>
        <p class="text-opacity-50 text-center leading-snug">
          I’m looking for any opportunities to help solving your problems,
          if you’re interested you can leave a message there and
          I’ll try my best to get it back to you. Also feel free to ask anything
          to me or just say hi by connect to my socials.
        </p>
      </div>
      <form class="mt-8 md:mt-0 md:w-1/2" @submit.prevent="">
        <label for="your-name" class="text-opacity-50 mb-1 inline-block">Name</label>
        <input
          class="bg-transparent border border-white border-opacity-25 rounded-sm
            py-3 px-2 mb-3 text-opacity-80 w-full"
          type="text"
          name="your-name"
          id="your-name"
        >
        <label for="your-email" class="text-opacity-50 mb-1 inline-block">Email Address</label>
        <input
          class="bg-transparent border border-white border-opacity-25 rounded-sm
            py-3 px-2 mb-3 text-opacity-80 w-full"
          type="email"
          name="your-email"
          id="your-email"
        >
        <label for="your-message" class="text-opacity-50 mb-1 inline-block">Text Message</label>
        <textarea
          class="bg-transparent border border-white border-opacity-25 rounded-sm
            py-3 px-2 mb-3 text-opacity-80 w-full"
          name="text-message"
          id="your-message"
          rows="5"
        ></textarea>
        <button
          class="py-3 px-6 border border-primary rounded-sm text-primary"
          type="submit"
        >
          Send message
        </button>
      </form>
    </div>
  </section>
</template>
