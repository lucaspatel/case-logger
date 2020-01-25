<template>
  <div
    class="flex justify-center items-center flex-grow h-12 bg-white border border-gray-400 rounded px-2 hover:cursor-pointer hover:bg-purple-100 focus:outline-none focus:border-purple-500"
    id="unit-option"
    :class="{'border-purple-500' : this.activeUnit === this.unit}"
    tabindex="0"
    @click="updateUnits"
    @keydown.space="updateUnits"
  >
    <div class="font-semibold">
      <span class="text-xl">{{ this.unit }}</span>
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