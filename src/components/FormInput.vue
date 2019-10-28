<template>
  <div class="flex flex-col w-full">
    <p>{{ title }}</p>
    <input v-model="model" class="border border-red-500" />
  </div>
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