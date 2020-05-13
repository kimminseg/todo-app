<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsData" v-bind:key="index">
        {{ todoItem }}
        <button v-on:click="removeItem(todoItem, index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['propsData'],
  methods: {
    removeItem: function(todoItem, index) {
      console.log('clicked', todoItem, index);
      this.$emit('remove', todoItem, index);
    },
  },
};
</script>

<style></style>
