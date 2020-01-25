<template>
  <input
    :type="type"
    class="appearance-none w-full h-12 pl-4 m-1 border border-gray-400 rounded"
    v-bind:value="model"
    v-on:input="$emit('input', $event.target.value)"
    :placeholder="title"
  />
</template>

<script>
export default {
  name: "FormInput",
  props: {
    title: String,
    type: {
      type: String,
      default: "text"
    },
    model: String
  },
  data() {
    return {};
  },
  methods: {}
};
</script>

<style>
</style>