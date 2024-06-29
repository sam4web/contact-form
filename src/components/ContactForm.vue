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
          <input type="text" name="first-name" id="first-name" value="John" />
        </div>
        <div class="input-container">
          <label for="last-name">last name</label>
          <input type="text" name="last-name" id="last-name" value="Appleseed" />
        </div>
      </div>

      <div class="input-container">
        <label for="email">email address</label>
        <input type="email" name="email" id="email" value="email@example.com" />
      </div>

      <!-- <div class="flex-section"></div> -->

      <div class="input-container">
        <label for="message">message</label>
        <textarea name="message" id="message"></textarea>
      </div>

      <div class="input-container flex items-center">
        <input type="checkbox" name="agreed" id="agreed" />
        <label for="agreed">I consent to being contacted by the team</label>
      </div>

      <button class="btn" type="submit">Submit</button>
    </div>
  </form>
</template>
