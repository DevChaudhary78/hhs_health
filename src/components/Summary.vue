<template>
  <h2>Summary</h2>
  <p>First Name: {{ formData.firstName }}</p>
  <p>Last Name: {{ formData.lastName }}</p>
  <p>Date of Birth: {{ formData.dateOfBirth }}</p>
  <p>Health Card Number: {{ formData.healthCard }}</p>
  <p>Gender: {{ formData.gender }}</p>
</template>

<style scoped>
h2 {
  text-decoration: underline;
  font-size: 2rem;
}

p {
  margin: 0.3rem 0;
}
</style>

<script>
export default {
  props: ['formData']
}
</script>
