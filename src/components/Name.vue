<template>
  <label for="firstName">First Name</label>
  <input v-model="formData.firstName" id="firstName" required type="text">

  <label for="lastName">Last Name: </label>
  <input v-model="formData.lastName" id="lastName" required type="text">
</template>

<script>
export default {
  props: ['formData']
}
</script>
