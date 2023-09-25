<template>
  <div>
    <h2>Child Component</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: String, // Define a prop named 'message' of type String
  },
};
</script>

<style scoped>
/* Add scoped CSS for this component if needed */
</style>
