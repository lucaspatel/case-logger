<template>
  <input v-model="model" class="w-full border border-red-500" :placeholder="title" />
</template>

<script>
export default {
  name: "FormInput",
  props: ["title", "model"],
  data() {
    return {
      message: "Try change me!"
    };
  },
  methods: {
    onClick() {
      this.message = "Here you go :)";
    }
  }
};
</script>

<style>
</style>