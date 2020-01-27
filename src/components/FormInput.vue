<template>
  <input
    :type="type"
    class="w-full h-12 pl-4 m-1 border border-gray-400 rounded appearance-none"
    :placeholder="title"
    :value="model"
    @input="$emit('input', $event.target.value)"
    required
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
  methods: {
    updateModel() {
      this.$emit("onUpdatemModel", this.model);
    }
  }
};
</script>

<style>
</style>