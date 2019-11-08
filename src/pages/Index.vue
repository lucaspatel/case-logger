<template onload="addDateListener()">
  <Layout>
    <div class="flex flex-wrap justify-center bg-gray-200">
      <div class="w-full sm:w-full md:w-1/2 lg:w-1/2 xl:w-1/3 px-2 bg-white">
        <header id="header">
          <h1 class="text-4xl mx-1 py-8">Case Logger</h1>
        </header>
        <form class="flex flex-col">
          <section class="flex flex-col mb-8" id="patient">
            <p class="mx-1">Patient</p>
            <div class="flex flex-row">
              <form-input title="Date" :model="date" type="datetime-local" id="date" onchange="allignDates()" ></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="MRN" :bind="mrn"></form-input>
              <form-input title="Initials" :bind="initials"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="Facility" :bind="facility"></form-input>
            </div>
          </section>
          <section class="flex flex-col mb-8" id="procedure">
            <p class="mx-1">Procedure</p>
            <div class="flex flex-row">
              <form-input id="anesthesiaStart" title="Anesthesia Start" :bind="anesthesiaStart" type="time"></form-input>
              <form-input title="Anesthesia End" :bind="anesthesiaEnd" type="time"></form-input>
            </div>
            <div class="block-template">
              <div class="flex flex-row">
                <form-input title="Block" :bind="blockNum"></form-input>
              </div>
              <div class="flex flex-row">
                <form-input title="Block Start" :bind="blockStart"></form-input>
                <form-input title="Block End" :bind="blockEnd"></form-input>
              </div>
            </div>
            <div class="line-template">
              <div class="flex flex-row">
                <form-input title="Line" :bind="lineNum"></form-input>
              </div>
              <div class="flex flex-row">
                <form-input title="Line Start" :bind="lineStart"></form-input>
                <form-input title="Line End" :bind="lineEnd"></form-input>
              </div>
            </div>
            <div class="inline-flex flex-row">
              <textarea
                :bind="notes"
                class="w-full h-24 m-1 mb-8 pl-4 pt-3 border border-gray-400 rounded"
                placeholder="Additional Notes"
              ></textarea>
            </div>
          </section>
          <section class="flex flex-col mb-8" id="controls">
            <div class="flex flex-row">
              <form-button message="Add Block/Line"></form-button>
              <form-button message="Remove Block/Line"></form-button>
            </div>
            <div class="flex flex-row">
              <form-button message="Save"></form-button>
            </div>
          </section>
        </form>
      </div>
    </div>
  </Layout>
</template>

<script>
import FormInput from "~/components/FormInput.vue";
import FormButton from "~/components/FormButton.vue";

export default {
  components: {
    FormInput: FormInput,
    FormButton: FormButton
  },
  data() {
    return {
      date: "12/02/1997",
      mrn: "",
      initials: "",
      facility: "",
      anesthesiaStart: "",
      anesthesiaEnd: "",
      blockLines: [],
      notes: ""
    };
  },
  methods: {
    addDateListener: function () {
      const $source = document.querySelector("#date");
      const $result = document.querySelector("#anesthesiaStart");

      const typeHandler = function(e) {
        $result.innerHTML = e.target.value;
      };

      $source.addEventListener("input", typeHandler); // register for oninput
      $source.addEventListener("propertychange", typeHandler); // for IE8
    }
  },
  metaInfo: {
    title: "Case Logger"
  }
};

</script>

<style>
.home-links a {
  margin-right: 1rem;
}
body {
  font-family: "Sarabun", sans-serif;
}
</style>
