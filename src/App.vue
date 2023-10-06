<template>
  <h1>Step {{ currentStep }}</h1>
  <form @submit.prevent="nextStep">
    <!-- used to dynamically render the component based on the return value from currentStepComponent -->
    <component :is="currentStepComponent" :formData="formData"></component>

    <!-- v-if/else is awesome, using which we can dynamically render components based on condition -->
    <button v-if="currentStep < 3">Next</button>
    <button v-else @click="resetForm">Start Over</button>
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

button {
  height: 40px;
  width: 100px;
  margin: 1rem auto;
  border: none;
  border-radius: 5px;

  font-weight: bold;
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
      }
    },
    resetForm() {
      this.currentStep = 1;
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
