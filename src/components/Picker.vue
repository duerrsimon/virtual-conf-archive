<template>
  <div class="hello">
    <h1 class="text-3xl mt-3 font-sans text-center bg-gray-200 py-2 font-light">
      Enter conference details
    </h1>
    <section class="text-gray-600 body-font">
      <div class="container px-5 mx-auto flex flex-wrap">
        <div class="flex relative pt-10 pb-20 sm:items-center md:w-2/3 mx-auto">
          <div
            class="h-full w-6 absolute inset-0 flex items-center justify-center"
          >
            <div class="h-full w-1 bg-gray-200 pointer-events-none"></div>
          </div>
          <div
            class="flex-shrink-0 w-6 h-6 rounded-full mt-10 sm:mt-0 inline-flex items-center justify-center bg-indigo-500 text-white relative z-10 title-font font-medium text-sm"
          >
            1
          </div>
          <div
            class="flex-grow md:pl-8 pl-6 flex sm:items-center items-start flex-col sm:flex-row"
          >
            <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
              <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
                Name your conference
              </h2>
              <t-input v-model="conference.name"></t-input>
            </div>
          </div>
        </div>
        <div class="flex relative pb-20 sm:items-center md:w-2/3 mx-auto">
          <div
            class="h-full w-6 absolute inset-0 flex items-center justify-center"
          >
            <div class="h-full w-1 bg-gray-200 pointer-events-none"></div>
          </div>
          <div
            class="flex-shrink-0 w-6 h-6 rounded-full mt-10 sm:mt-0 inline-flex items-center justify-center bg-indigo-500 text-white relative z-10 title-font font-medium text-sm"
          >
            2
          </div>
          <div
            class="flex-grow md:pl-8 pl-6 flex sm:items-center items-start flex-col sm:flex-row"
          >
            <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
              <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
                When will it happen or has it happend?
              </h2>
              <p class="leading-relaxed">
                You can collect information both for past and present meetings.
              </p>
              <div class="w-full">
                <datepicker
                  dateFormat="c"
                  range="true"
                  v-model="conference.date"
                ></datepicker>
              </div>
            </div>
          </div>
        </div>
        <div class="flex relative pb-20 sm:items-center md:w-2/3 mx-auto">
          <div
            class="h-full w-6 absolute inset-0 flex items-center justify-center"
          >
            <div class="h-full w-1 bg-gray-200 pointer-events-none"></div>
          </div>
          <div
            class="flex-shrink-0 w-6 h-6 rounded-full mt-10 sm:mt-0 inline-flex items-center justify-center bg-indigo-500 text-white relative z-10 title-font font-medium text-sm"
          >
            3
          </div>
          <div
            class="flex-grow md:pl-8 pl-6 flex sm:items-center items-start flex-col sm:flex-row"
          >
            <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
              <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
                Website & Location
              </h2>
              <div class="flex items-center space-x-2 py-3">
                <t-input
                  v-model="conference.website"
                  placeholder="https://conference.com"
                ></t-input>
                <div class="flex">
                  <label class="flex items-center">
                    <t-checkbox
                      name="virtual"
                      v-model="conference.virtual"
                    ></t-checkbox>
                    <span class="ml-2 text-sm">Virtual</span>
                  </label>
                </div>
              </div>

              <t-input
                placeholder="Location"
                v-model="conference.location"
                v-if="!conference.virtual"
              ></t-input>
            </div>
          </div>
        </div>
        <div class="flex relative pb-10 sm:items-center md:w-2/3 mx-auto">
          <div
            class="h-full w-6 absolute inset-0 flex items-center justify-center"
          >
            <div class="h-full w-1 bg-gray-200 pointer-events-none"></div>
          </div>
          <div
            class="flex-shrink-0 w-6 h-6 rounded-full mt-10 sm:mt-0 inline-flex items-center justify-center bg-indigo-500 text-white relative z-10 title-font font-medium text-sm"
          >
            4
          </div>
          <div
            class="flex-grow md:pl-8 pl-6 flex sm:items-center items-start flex-col sm:flex-row"
          >
            <div
              class="flex-shrink-0 w-24 h-24 bg-indigo-100 text-indigo-500 rounded-full inline-flex items-center justify-center"
            >
              <svg
                fill="none"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-12 h-12"
                viewBox="0 0 24 24"
              >
                <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"></path>
                <circle cx="12" cy="7" r="4"></circle>
              </svg>
            </div>
            <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
              <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
                Import CSV of participants
              </h2>
              <p>
                Download the
                <a
                  class="text-indigo-500 hover:underline"
                  href="/csv-sample.csv"
                  >sample csv</a
                >
                file to import your participants.
              </p>
              <vue-csv-import
                v-model="conference.csv"
                :autoMatchFields="true"
                :autoMatchIgnoreCase="true"
                :map-fields="['name', 'email']"
                submitBtnText="Test"
                checkboxClass=""
              >
                <template slot="hasHeaders" slot-scope="{ headers, toggle }">
                  <div class="flex space-x-2 items-center py-2">
                    <t-checkbox :value="headers" @change="toggle"> </t-checkbox>
                    <label> Are Headers present? </label>
                  </div>
                </template>
                <template slot="thead">
                  <tr>
                    <th>Fields</th>
                    <th>Column</th>
                  </tr>
                </template>
                <template slot="next" slot-scope="{ load }">
                  <button
                    class="my-2 text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg"
                    @click.prevent="load"
                  >
                    Import
                  </button>
                </template>
              </vue-csv-import>

              <div v-if="conference.csv.length > 0">
                <h5 class="text-lg mt-4">Preview of particpants</h5>

                <t-table
                  :headers="['Name', 'Email']"
                  :data="previewCsv"
                ></t-table>

                <div class="w-full text-right">
                  <span class="text-sm">
                    Showing {{ previewCsv.length }} of
                    {{ conference.csv.length }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <div class="text-xl text-center bg-gray-200 py-8 font-light">
      <p class="py-2">Okay, ready to archive!</p>
      <p class="pb-2 text-sm">
        You will need to sign-in using your ORCID in the next step to continue.
      </p>
      <button
        class="text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg"
      >
        Continue
      </button>
    </div>
  </div>
</template>

<script>
import { VueCsvImport } from "vue-csv-import";

export default {
  name: "Picker",
  props: {},
  components: { VueCsvImport },
  computed: {
    previewCsv() {
      if (this.conference.csv) {
        return this.conference.csv.slice(0, 2);
      } else {
        return [];
      }
    },
  },
  data() {
    return {
      conference: {
        name: "",
        date: null,
        website: "",
        location: "",
        virtual: false,
        csv: [],
      },
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
