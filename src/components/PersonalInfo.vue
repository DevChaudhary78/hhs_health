<template>
  <div>
    <label for="dateOfBirth">Date of Birth:</label>
    <input v-model="formData.dateOfBirth" type="text" id="dateOfBirth" required>

    <label for="healthCard">Health Card Number: </label>
    <input v-model="formData.healthCard" type="text" id="healthCard" required>

    <label for="gender">Gender: </label>
    <select v-model="formData.gender" name="gender" id="gender" required>
      <option value="male">Male</option>
      <option value="female">Female</option>
      <option value="other">Other</option>
    </select>
  </div>
</template>

<script>
export default {
  props: ['formData']
}
</script>

