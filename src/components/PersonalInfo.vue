<template>
  <label for="dateOfBirth">Date of Birth:</label>
  <input v-model="formData.dateOfBirth" type="text" id="dateOfBirth" required>

  <label for="healthCard">Health Card Number: </label>
  <input @input="luhnAlgorithmHCNChecker" v-model="formData.healthCard" type="text" id="healthCard" required>
  <p v-if="isValidHealthCard">Valid ✅</p>
  <p v-else>Invalid ❌</p>

  <label for="gender">Gender: </label>
  <select v-model="formData.gender" name="gender" id="gender" required>
    <option value="" selected hidden disabled>Choose</option>
    <option value="male" selected="selected">Male</option>
    <option value="female">Female</option>
    <option value="other">Other</option>
  </select>
</template>

<style>
input {
  margin-bottom: 1rem;
}
</style>

<script>
export default {
  props: ['formData'],

  data() {
    return {
      isValidHealthCard: false,
    }
  },

  methods: {
    luhnAlgorithmHCNChecker() {
      const healthCardNumberStr = this.formData.healthCard.replace(/\s+/g, ''); // removing any spaces using regex
      const length = healthCardNumberStr.length;

      if (length != 10) {
        this.isValidHealthCard = false;
        return;
      }

      let sum = 0;

      for (let i = length - 2; i >= 0; i -= 2) {
        let currentNum = parseInt(healthCardNumberStr[i], 10);
        currentNum *= 2;
        if (currentNum > 9) {
          currentNum -= 9;
        }

        sum += currentNum;
      }

      for (let i = length - 1; i >= 0; i -= 2) {
        sum += parseInt(healthCardNumberStr[i], 10);
      }

      this.isValidHealthCard = sum % 10 === 0;
    }
  }
};

</script>

