<script setup>
import { watch } from 'vue'

const props = defineProps(['showModal'])
const emits = defineEmits(['hideModal'])

watch(
  () => props.showModal,
  (newVal) => {
    if (newVal) setInterval(() => emits('hideModal'), 1500)
  }
)
</script>

<template>
  <section class="absolute top-[3.25%] px-2 z-[2]" :class="{ hidden: !props.showModal }">
    <div class="modal-container space-y-2.5">
      <div class="flex items-center space-x-3">
        <img src="@/assets/icons/success-check.svg" alt="success-icon" />
        <h3>message sent!</h3>
      </div>
      <p>Thanks for completing the form. We'll be in touch soon!</p>
    </div>
  </section>
</template>
