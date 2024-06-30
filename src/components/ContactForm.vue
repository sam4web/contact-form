<script setup>
import { reactive, ref } from 'vue'

const emits = defineEmits(['formSubmit'])

const errors = ref({})
const formData = reactive({
  firstName: '',
  lastName: '',
  email: '',
  queryType: '',
  message: '',
  checked: false
})

function validateEmail(email) {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return emailRegex.test(email)
}

function checkSelected(value) {
  return value === formData.queryType
}

function resetForm() {
  formData.firstName = ''
  formData.lastName = ''
  formData.email = ''
  formData.queryType = ''
  formData.message = ''
  formData.checked = false
}

function validateForm() {
  errors.value = {}
  const requiredFields = ['firstName', 'lastName', 'email', 'queryType', 'message']
  requiredFields.forEach((field) => {
    if (!formData[field]) errors.value[field] = 'This field is required'
  })
  if (formData.email && !validateEmail(formData.email))
    errors.value.email = 'Please enter a valid email address'
  if (!formData.checked)
    errors.value.checked = 'To submit this form, please consent to being contacted'
}

function submitForm() {
  validateForm()
  if (Object.keys(errors.value).length !== 0) return
  emits('formSubmit')
  resetForm()
}
</script>

<template>
  <form @submit.prevent="submitForm" class="form-container">
    <div class="section-spacing space-y-5 md:space-y-8">
      <h2 class="heading">contact us</h2>

      <div class="flex-section">
        <div class="input-container">
          <label for="first-name">first name</label>
          <input
            :class="{ 'input-error': errors.firstName }"
            type="text"
            name="first-name"
            id="first-name"
            v-model="formData.firstName"
          />
          <p class="error-text">{{ errors.firstName }}</p>
        </div>
        <div class="input-container">
          <label for="last-name">last name</label>
          <input
            :class="{ 'input-error': errors.lastName }"
            type="text"
            name="last-name"
            id="last-name"
            v-model="formData.lastName"
          />
          <p class="error-text">{{ errors.lastName }}</p>
        </div>
      </div>

      <div class="input-container">
        <label for="email">email address</label>
        <input
          :class="{ 'input-error': errors.email }"
          type="email"
          name="email"
          id="email"
          v-model="formData.email"
        />
        <p class="error-text">{{ errors.email }}</p>
      </div>

      <div class="input-container">
        <label>query type</label>
        <div class="flex-section md:space-y-0 space-y-3">
          <label
            :class="{ 'input-radio-selected': checkSelected('general-enquiry') }"
            class="input-radio"
            for="general-enquiry"
          >
            <input
              type="radio"
              name="query-type"
              id="general-enquiry"
              value="general-enquiry"
              v-model="formData.queryType"
            />
            <p>General Enquiry</p>
          </label>

          <label
            :class="{ 'input-radio-selected': checkSelected('support-request') }"
            class="input-radio"
            for="support-request"
          >
            <input
              type="radio"
              name="query-type"
              id="support-request"
              value="support-request"
              v-model="formData.queryType"
            />
            <p>Support Request</p>
          </label>
        </div>
        <p class="error-text">{{ errors.queryType }}</p>
      </div>

      <div class="input-container">
        <label for="message">message</label>
        <textarea
          :class="{ 'input-error': errors.message }"
          name="message"
          id="message"
          v-model="formData.message"
        ></textarea>
        <p class="error-text">{{ errors.message }}</p>
      </div>

      <div class="input-container">
        <div class="flex items-center space-x-4">
          <input type="checkbox" name="checked" id="checked" v-model="formData.checked" />
          <label for="checked">I consent to being contacted by the team</label>
        </div>
        <p class="error-text">{{ errors.checked }}</p>
      </div>

      <button class="btn" type="submit">Submit</button>
    </div>
  </form>
</template>
