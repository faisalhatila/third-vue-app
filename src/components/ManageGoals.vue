<template>
  <h2>Manage Goals</h2>
  <input type="text" ref="goal" />
  <button @click="setGoal">Set Goal</button>
  <teleport to="body">
    <error-alert v-if="inputIsValid">
      <h2>Input is invald</h2>
      <p>Please enter at least a few characters...</p>
      <button @click="confirmGoal">Okay</button>
    </error-alert>
  </teleport>
</template>

<script>
import ErrorAlert from "./ErrorAlert";

export default {
  components: {
    ErrorAlert,
  },
  data() {
    return {
      inputIsValid: false,
    };
  },
  methods: {
    setGoal() {
      const enteredValue = this.$refs.goal.value;
      if (enteredValue === "") {
        this.inputIsValid = true;
        return;
      } else {
        this.inputIsValid = false;
        return;
      }
    },
    confirmGoal() {
      this.inputIsValid = false;
    },
  },
};
</script>

<style lang="scss" scoped></style>
