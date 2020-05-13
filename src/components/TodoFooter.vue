<template>
  <div>
    <button v-on:click="clearTodoItems">clear</button>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodoItems: function() {
      this.$emit('clear');
    },
  },
};
</script>
<style></style>
