<template>
  <section class="text-gray-600 body-font">
    <div
      class="container mx-auto flex px-5 py-24 md:flex-row flex-col items-center"
    >
      <div
        class="lg:flex-grow md:w-1/2 lg:pr-24 md:pr-16 flex flex-col md:items-start md:text-left mb-16 md:mb-0 items-center text-center"
      >
        <h1
          class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900"
        >
          Archive your conference
        </h1>
        <p class="mb-8 leading-relaxed">
          Get a DOI for each poster or talk presented at the conference and
          archive the material for free. Just import a CSV file from any source
          and attendees will get an email to upload their material.
        </p>
        <div class="flex justify-center">
          <button
            @click="$emit('showDetails')"
            class="inline-flex text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg items-center"
          >
            <span> Get started now</span>
            <svg
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              class="w-6 h-6 ml-1"
              viewBox="0 0 24 24"
            >
              <path d="M5 12h14M12 5l7 7-7 7"></path>
            </svg>
          </button>
        </div>
      </div>
      <div class="lg:max-w-lg lg:w-full md:w-1/2 w-5/6">
        <img
          class="object-cover object-center rounded"
          alt="hero"
          src="/undraw_urban_design_kpu8.svg"
        />
      </div>
    </div>
  </section>
</template>