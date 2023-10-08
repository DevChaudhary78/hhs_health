<template>
  <h1>Step {{ currentStep }}</h1>
  <form @submit.prevent="nextStep">
    <!-- used to dynamically render the component based on the return value from currentStepComponent -->
    <component :is="currentStepComponent" :currentStep="currentStep" :formData="formData"></component>

  </form>
</template>

<style scoped>
form {
  border: 1px solid #457b9d;
  border-radius: 0.2rem;
  max-width: 30rem;
  padding: 3rem;
  background: #a8dadc;

  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>

<script>
import Name from "./components/Name.vue"
import PersonalInfo from "./components/PersonalInfo.vue";
import Summary from "./components/Summary.vue";

export default {
  // we don't need to export those Components for now, but I am thinking
  // of a situation when we needed them to render from the Main component so.
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
      }
    }
  },

  methods: {
    nextStep() {
      if (this.currentStep < 3) {
        this.currentStep++;
      } else {
        // I am thinking about making a web server using Go lang or Rust to store this data into databsae (:
        this.currentStep = 1;
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
