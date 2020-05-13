<template>
  <div>
    <input v-model="inputText" type="text" />
    <button v-on:click="addItem()">add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
    };
  },
  addItem: function() {
    var value = this.inputText;
    this.emit('add', value);
    this.clearInput();
  },
  clearInput: function() {
    this.inputText = '';
  },
};
</script>

<style></style>
