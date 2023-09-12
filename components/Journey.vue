<template>
  <div class="mt-10">
    <h4 class="mt-6 text-4xl text-gray-900 font-bold">
      The Journey<span class="text-sky-400">!</span>
    </h4>
    42 <ul class="mt-6 border-l border-gray-200">
      <li v-for="job in resume.work" :key="job.id" class="mb-10 ml-6 relative">
        <span class="absolute -left-9 top-0.5 w-6 h-6 bg-sky-400 dark:bg-sky-400 rounded-full" />
        <div class="flex justify-between">
          <h6 class="text-lg text-gray-800">
            {{ job.position }} @ {{ job.company }}
          </h6>
          <time class="text-gray-400 block">{{ job?.startDate }} - {{ job?.endDate }}</time>
        </div>
<!--        <p class="text-gray-500 md:text-justify print:text-justify">-->
<!--          {{ job.summary }}-->
<!--          <a class="text-sky-400 hover:underline print:hidden" :href="`/job-details/${job.id}`">Details</a>-->
<!--        </p>-->
        <ul>
          <li v-for="highlight in job.highlights" class="text-gray-500 md:text-justify print:text-justify">
            <span class="text-sky-400 text-xl font-bold">-</span> {{ highlight }}
          </li>
        </ul>
      </li>
      <li v-for="college in resume.education" :key="college.id" class="mb-10 ml-6 relative">
        <span class="absolute -left-9 top-0.5 w-6 h-6 bg-sky-400 dark:bg-sky-400 rounded-full" />
        <div class="flex justify-between">
          <h6 class="text-lg text-gray-800">
            {{ college.studyType }} in {{ college.area }}
          </h6>
          <time class="text-gray-400">{{ college?.startDate }} - {{ college?.endDate }}</time>
        </div>
        <p class="text-gray-500 md:text-justify">
          {{ college.location }}
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    resume: Object
  }
};
</script>

