<template>
  <div class="flex-grow m-1">
    <input
      type="number"
      :class="{'border-purple-500' : this.activeUnit === customUnit}"
      class="flex w-full h-12 font-semibold text-center border border-gray-400 rounded appearance-none hover:cursor-pointer hover:bg-purple-100 focus:border-purple-500 unit-option"
      v-model.number="customUnit"
      @click="updateUnits"
      @change="updateUnits"
      @focusout="clear"
      tabindex="0"
      placeholder="Units"
      required
    />
  </div>
</template>

<script>
export default {
  model: {
    prop: "activeUnit",
    event: "onUpdateUnit"
  },
  props: ["options", "activeUnit"],
  data() {
    return {
      customUnit: "",
      lastUnit: this.activeUnit
    };
  },
  methods: {
    updateUnits() {
      this.$emit("onUpdateUnit", this.customUnit);
    },
    clear() {
      if (this.customUnit === "") this.activeUnit = this.lastUnit;
      if (this.options.includes(this.customUnit)) this.customUnit = "";
    }
  }
};
</script>