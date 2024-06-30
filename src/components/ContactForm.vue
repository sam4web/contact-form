<script setup>
function handleSubmit() {
  console.log('Submitted !')
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="form-container">
    <div class="section-spacing">
      <h2 class="heading">contact us</h2>

      <div class="flex-section">
        <div class="input-container">
          <label for="first-name">first name</label>
          <input class="input-error" type="text" name="first-name" id="first-name" value="John" />
          <p class="error-text">This field is required</p>
        </div>
        <div class="input-container">
          <label for="last-name">last name</label>
          <input
            class="input-error"
            type="text"
            name="last-name"
            id="last-name"
            value="Appleseed"
          />
          <p class="error-text">This field is required</p>
        </div>
      </div>

      <div class="input-container">
        <label for="email">email address</label>
        <input class="input-error" type="email" name="email" id="email" value="email@example.com" />
        <p class="error-text">Please enter a valid email address</p>
      </div>

      <div class="input-container">
        <label>query type</label>
        <div class="flex-section">
          <div class="input-radio">
            <input type="radio" name="query-type" id="general-enquiry" />
            <label for="general-enquiry">General Enquiry</label>
          </div>
          <div class="input-radio">
            <input type="radio" name="query-type" id="support-request" />
            <label for="support-request">Support Request</label>
          </div>
        </div>
        <p class="error-text">Please select a query type</p>
      </div>

      <div class="input-container">
        <label for="message">message</label>
        <textarea class="input-error" name="message" id="message"></textarea>
        <p class="error-text">This field is required</p>
      </div>

      <div class="input-container">
        <div class="flex items-center space-x-4">
          <input type="checkbox" name="agreed" id="agreed" />
          <label for="agreed">I consent to being contacted by the team</label>
        </div>
        <p class="error-text">To submit this form, please consent to being contacted</p>
      </div>

      <button class="btn" type="submit">Submit</button>
    </div>
  </form>
</template>
