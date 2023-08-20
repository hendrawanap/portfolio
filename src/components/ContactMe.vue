<script setup>
import emailjs from '@emailjs/browser';
import { reactive, ref } from 'vue';

const { VITE_EMAIL_SERVICE_ID, VITE_EMAIL_TEMPLATE_ID, VITE_EMAIL_USER_ID } = import.meta.env;

const formRef = ref(null);
const showAlert = ref(false);
const alertType = ref(null);
const form = reactive({
  name: '',
  email: '',
  message: '',
});

const triggerAlert = (type) => {
  showAlert.value = true;
  alertType.value = type;
  setTimeout(() => {
    showAlert.value = false;
    alertType.value = type;
  }, 3000);
};

const resetForm = () => {
  form.name = '';
  form.email = '';
  form.message = '';
};

const sendMessage = () => {
  emailjs
    .sendForm(VITE_EMAIL_SERVICE_ID, VITE_EMAIL_TEMPLATE_ID, formRef.value, VITE_EMAIL_USER_ID)
    .then(
      () => {
        triggerAlert('success');
        resetForm();
      },
      () => {
        triggerAlert('error');
      },
    );
};
</script>

<template>
  <section>
    <div class="flex items-center mb-8 w-full" data-aos="fade">
      <svg class="mr-3 mt-1" height="2" width="32">
        <line class="stroke-primary stroke-2" x1="0" y1="0" x2="32" y2="0" />
      </svg>
      <h4 class="text-opacity-80">More Info.</h4>
    </div>
    <div class="flex flex-col md:flex-row md:pl-10">
      <div class="md:mr-10 md:w-1/2" data-aos="fade">
        <h4 class="text-opacity-80 text-center mb-2">Get In Touch.</h4>
        <p class="text-opacity-50 text-center leading-snug">
          I’m looking for any opportunities to help solving your problems, if you’re interested you
          can leave a message there and I’ll try my best to get it back to you. Also feel free to
          ask anything to me or just say hi by connect to my socials.
        </p>
      </div>
      <form
        class="mt-8 md:mt-0 md:w-1/2 overflow-hidden"
        @submit.prevent="sendMessage"
        ref="formRef"
        data-aos="fade"
      >
        <label for="your-name" class="text-opacity-50 mb-1 inline-block">Name</label>
        <input
          class="bg-transparent border border-white border-opacity-25 rounded-sm py-3 px-2 mb-3 text-opacity-80 w-full"
          type="text"
          name="from_name"
          id="your-name"
          v-model="form.name"
          required
        />
        <label for="your-email" class="text-opacity-50 mb-1 inline-block">Email Address</label>
        <input
          class="bg-transparent border border-white border-opacity-25 rounded-sm py-3 px-2 mb-3 text-opacity-80 w-full"
          type="email"
          name="from_email"
          id="your-email"
          v-model="form.email"
          required
        />
        <label for="your-message" class="text-opacity-50 mb-1 inline-block">Text Message</label>
        <textarea
          class="bg-transparent border border-white border-opacity-25 rounded-sm py-3 px-2 mb-4 text-opacity-80 w-full"
          name="message"
          id="your-message"
          rows="5"
          v-model="form.message"
          required
        ></textarea>
        <div class="flex flex-col items-start sm:flex-row sm:items-center">
          <button
            class="flex border border-primary rounded-sm disabled:opacity-40"
            type="submit"
            :disabled="showAlert"
          >
            <span
              class="py-3 px-6 text-primary ring-1 ring-primary bg-black transition-transform hover:-translate-x-1 hover:-translate-y-1"
            >
              Send message
            </span>
          </button>
          <p
            v-if="alertType === 'success'"
            class="mt-3 sm:mt-0 sm:ml-8 bg-opacity-25 bg-green-600 py-2 px-4 rounded-full text-opacity-80 transition-all"
            :class="[showAlert ? '' : 'duration-700 opacity-0']"
          >
            Message Sent.
          </p>
          <p
            v-if="alertType === 'error'"
            class="mt-3 sm:mt-0 sm:ml-8 bg-opacity-25 bg-red-600 py-2 px-4 rounded-full text-opacity-80 transition-all"
            :class="[showAlert ? '' : 'duration-700 opacity-0']"
          >
            Error occured.
          </p>
        </div>
      </form>
    </div>
  </section>
</template>
