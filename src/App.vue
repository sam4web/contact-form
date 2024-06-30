<script setup>
import { ref } from 'vue'

import ContactForm from '@/components/ContactForm.vue'
import SuccessModal from '@/components/SuccessModal.vue'

const showModal = ref(false)
</script>

<template>
  <main className="size-full min-h-screen flex-center relative">
    <SuccessModal :showModal="showModal" />
    <div class="w-full section-spacing">
      <div class="max-w-[820px] mx-auto w-full">
        <ContactForm />
      </div>
    </div>
  </main>
</template>
