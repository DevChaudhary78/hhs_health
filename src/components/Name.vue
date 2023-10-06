<template>
  <label for="firstName">First Name: </label>
  <!-- v-models are awesome, we can bind the value directly to the specified data (; -->
  <input v-model="formData.firstName" id="firstName" required type="text">

  <label for="lastName">Last Name: </label>
  <input v-model="formData.lastName" id="lastName" required type="text">
</template>

<style scoped>
input {
  margin-bottom: 1rem;
}
</style>


<script>
export default {
  props: ['formData']
}
</script>
