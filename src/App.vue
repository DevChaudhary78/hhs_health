<template>
  <h1>Step {{ currentStep }}</h1>
  <form @submit.prevent="nextStep">
    <component :is="currentStepComponent" :formData="formData"></component>

    <button v-if="currentStep < 3" type="submit">Next</button>
    <button v-else @click="resetForm">Start Over</button>
  </form>
</template>

<script>
import Name from "./components/Name.vue"
import PersonalInfo from "./components/PersonalInfo.vue";
import Summary from "./components/Summary.vue";

export default {
  components: {
    Name,
    PersonalInfo,
    Summary,
  },

  data() {
    return {
      currentStep: 1,
      formData: {
        firstName: '',
        lastName: '',
        dateOfBirth: '',
        healthCard: '',
        gender: '',
      },
    };
  },

  computed: {
    currentStepComponent() {
      switch (this.currentStep) {
        case 1:
          return 'Name';
        case 2:
          return 'PersonalInfo';
        case 3:
          return 'Summary';
        default:
          return '';
      }
    }
  },

  methods: {
    nextStep() {
      if (this.currentStep < 3) {
        this.currentStep++;
      } else {
        // Handle final form submission (e.g., sending data to the server)
      }
    },
    resetForm() {
      this.currentStep = 0;
      this.formData = {
        firstName: '',
        lastName: '',
        dateOfBirth: '',
        healthCard: '',
        gender: '',
      }
    }
  },

}
</script>
