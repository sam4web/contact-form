<script setup>
import { reactive } from 'vue'

const formData = reactive({
  firstName: '',
  lastName: '',
  email: '',
  queryType: '',
  message: '',
  checked: false
})

function checkSelected(value) {
  return value === formData.queryType
}

function handleSubmit() {
  console.log(JSON.stringify(formData))
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="form-container">
    <div class="section-spacing">
      <h2 class="heading">contact us</h2>

      <div class="flex-section">
        <div class="input-container">
          <label for="first-name">first name</label>
          <input type="text" name="first-name" id="first-name" v-model="formData.firstName" />
          <!-- <p class="error-text">This field is required</p> -->
        </div>
        <div class="input-container">
          <label for="last-name">last name</label>
          <input type="text" name="last-name" id="last-name" v-model="formData.lastName" />
          <!-- <p class="error-text">This field is required</p> -->
        </div>
      </div>

      <div class="input-container">
        <label for="email">email address</label>
        <input type="email" name="email" id="email" v-model="formData.email" />
        <!-- <p class="error-text">Please enter a valid email address</p> -->
      </div>

      <div class="input-container">
        <label>query type</label>
        <div class="flex-section">
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
        <!-- <p class="error-text">Please select a query type</p> -->
      </div>

      <div class="input-container">
        <label for="message">message</label>
        <textarea name="message" id="message" v-model="formData.message"></textarea>
        <!-- <p class="error-text">This field is required</p> -->
      </div>

      <div class="input-container">
        <div class="flex items-center space-x-4">
          <input type="checkbox" name="checked" id="checked" v-model="formData.checked" />
          <label for="checked">I consent to being contacted by the team</label>
        </div>
        <!-- <p class="error-text">To submit this form, please consent to being contacted</p> -->
      </div>

      <button class="btn" type="submit">Submit</button>
    </div>
  </form>
</template>
