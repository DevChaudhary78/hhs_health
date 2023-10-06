<template>
  <h2>Summary</h2>
  <p><span>Name:</span> {{ formData.firstName }} {{ formData.lastName }}</p>
  <p><span>Date of Birth:</span> {{ formData.dateOfBirth }}</p>
  <p><span>Health Card Number:</span> {{ formData.healthCard }}</p>
  <p><span>Gender:</span> {{ formData.gender }}</p>
</template>

<style scoped>
h2 {
  text-decoration: underline;
  font-size: 2rem;
}

span {
  font-weight: bold;
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
