<template>
  <h2>Summary</h2>
  <p>First Name: {{ formData.firstName }}</p>
  <p>Last Name: {{ formData.lastName }}</p>
  <p>Date of Birth: {{ formData.dateOfBirth }}</p>
  <p>Health Card Number: {{ formData.healthCard }}</p>
  <p>Gender: {{ formData.gender }}</p>
</template>

<script>
export default {
  props: ['formData']
}
</script>
