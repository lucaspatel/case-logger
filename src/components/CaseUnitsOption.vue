<template>
  <div
    class="flex items-center justify-center flex-grow h-12 m-1 border border-gray-400 rounded hover:cursor-pointer hover:bg-purple-100 focus:outline-none focus:border-purple-500 unit-option"
    :class="{ 'border-purple-500': this.activeUnit === this.unit }"
    tabindex="0"
    @click="updateUnits"
    @keydown.space="updateUnits"
  >
    <div class="font-semibold">
      <span>{{ this.unit }}</span>
    </div>
  </div>
</template>

<script>
export default {
  model: {
    prop: "activeUnit",
    event: "onUpdateUnit"
  },
  props: ["unit", "activeUnit"],
  methods: {
    updateUnits() {
      this.$emit("onUpdateUnit", this.unit);
    }
  }
};
</script>