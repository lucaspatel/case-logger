<template>
  <Layout>
    <div class="flex flex-wrap justify-center bg-gray-200">
      <div class="w-full px-2 bg-white sm:w-full md:w-1/2 lg:w-1/2 xl:w-1/3">
        <header id="header">
          <h1 class="pt-8 pb-16 mx-1 text-4xl">Case Logger</h1>
        </header>
        <form class="flex flex-col">
          <section class="flex flex-col mb-8" id="patient">
            <p class="mx-1">Patient</p>
            <div class="flex flex-row">
              <form-input
                title="Date"
                type="date"
                v-model="form.date"
              ></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="MRN" v-model="form.patient.mrn"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input
                title="Initials"
                v-model="form.patient.firstName"
              ></form-input>
              <form-input title="Facility" v-model="form.facility"></form-input>
            </div>
          </section>
          <section class="flex flex-col">
            <p class="mx-1">Procedure</p>
            <div class="flex flex-row">
              <form-input
                title="Case Description"
                v-model="form.case"
              ></form-input>
            </div>
            <div class="flex flex-row flex-wrap justify-between" id="units">
              <case-units-option
                v-for="unit in unitDefaults"
                :key="unit"
                :unit="unit"
                v-model="form.units"
              ></case-units-option>
              <custom-case-units-option
                :options="unitDefaults"
                v-model.number="form.units"
              ></custom-case-units-option>
            </div>
            <div class="flex flex-row">
              <form-input
                title="Anesthesia Start"
                type="time"
                v-model="form.anestStart"
              ></form-input>
              <form-input
                title="Anesthesia End"
                type="time"
                v-model="form.anestEnd"
              ></form-input>
              <label class="w-full h-12 pt-3 m-1 text-center text-gray-500">
                <!--prettier-ignore-->
                {{ minutes }} minute<span v-if="minutes !== 1">s</span>
              </label>
            </div>
            <block-line-group
              v-for="bl in form.blockLines"
              :key="bl.id"
              :bl="bl"
              :id="bl.id"
            ></block-line-group>
          </section>
          <div class="flex-row pr-2">
            <textarea
              v-model="form.notes"
              class="w-full h-24 px-4 pt-3 m-1 mb-8 border border-gray-400 rounded appearance-none"
              placeholder="Additional Notes"
            ></textarea>
          </div>
          <section class="flex flex-col pb-4" id="controls">
            <div class="flex justify-center">
              <form-button
                class="w-1/2 m-1"
                :action="addBL"
                :disabled="form.blockLines.length >= 3"
                >Add Block / Line</form-button
              >
              <form-button
                class="w-1/2 m-1"
                :action="removeBL"
                :disabled="form.blockLines.length <= 0"
                >Remove Block / Line</form-button
              >
            </div>
            <form-button class="m-1" :action="save">Save</form-button>
          </section>
        </form>
      </div>
    </div>
  </Layout>
</template>

<script>
import FormInput from "~/components/FormInput.vue";
import FormButton from "~/components/FormButton.vue";
import BlockLineGroup from "~/components/BlockLineGroup.vue";
import CaseUnitsOption from "~/components/CaseUnitsOption.vue";
import CustomCaseUnitsOption from "~/components/CustomCaseUnitsOption.vue";

import clipboard from "clipboard-copy";

export default {
  components: {
    FormInput: FormInput,
    FormButton: FormButton,
    BlockLineGroup: BlockLineGroup,
    CaseUnitsOption: CaseUnitsOption,
    CustomCaseUnitsOption: CustomCaseUnitsOption
  },
  data() {
    return {
      blMax: "3",
      unitDefaults: [1, 2, 3],
      form: {
        facility: "SRMC",
        case: "",
        units: "",
        date: this.getDate(),
        anestStart: this.getTime(),
        anestEnd: this.getTime(),
        notes: "",
        patient: {
          initials: "",
          mrn: ""
        },
        blockLines: []
      }
    };
  },
  computed: {
    minutes() {
      let diff =
        Date.parse(this.form.date + "T" + this.form.anestEnd) -
        Date.parse(this.form.date + "T" + this.form.anestStart);
      return diff / 60000;
    }
  },
  methods: {
    save() {
      console.log(JSON.stringify(this.form, null, 2));
      clipboard(JSON.stringify(this.form, null, 2));
    },
    addBL() {
      let nextId = this.form.blockLines.length + 1;
      let nextObj = {
        id: nextId,
        name: "",
        value: "",
        start: "",
        end: ""
      };
      this.form.blockLines.push(nextObj);
    },
    removeBL() {
      this.form.blockLines.pop();
    },
    getDate() {
      let d = new Date(),
        month = "" + (d.getMonth() + 1),
        day = "" + d.getDate(),
        year = d.getFullYear();
      if (month.length < 2) month = "0" + month;
      if (day.length < 2) day = "0" + day;

      return [year, month, day].join("-");
    },
    getTime() {
      let d = new Date(),
        hour = "" + d.getHours(),
        minute = "" + d.getMinutes();
      if (hour.length < 2) hour = "0" + hour;
      if (minute.length < 2) minute = "0" + minute;

      return [hour, minute].join(":");
    }
  },
  metaInfo: {
    title: "Case Logger"
  }
};
</script>

<style lang="css">
body {
  font-family: "Sarabun", sans-serif;
}
</style>
