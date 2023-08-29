<template>
  <div class="max-w-screen-lg md:flex mx-auto">
    <div class="hidden md:block md:w-[325px]">
      <AuthorCard :resume="resume" />
    </div>
    <div class="md:w-2/3">
      <div class="pt-6 mb-6">
        <h1 class="text-4xl text-gray-900 font-bold">
          {{ job.position }} <span class="text-sky-400">@</span> {{ job.company }}
        </h1>
        <time class="text-gray-400">{{ job?.startDate }} - {{ job?.endDate }}</time>
      </div>
      <h6 class="mb-6 text-lg text-gray-800">
        The Company<span class="text-sky-400">_</span>
      </h6>
      <p class="mb-6 text-gray-500 md:text-justify print:text-justify">
        {{ job?.company_bio }}
      </p>
      <h6 class="mb-6 text-lg text-gray-800">
        The Role<span class="text-sky-400">_</span>
      </h6>
      <ul>
        <li v-for="highlight in job.highlights" class="mb-6 text-gray-500 md:text-justify print:text-justify">
          <span class="text-sky-400 text-xl font-bold">•</span> {{ highlight }}
        </li>
      </ul>
      <p>
        <a @click="back" class="text-sky-400 hover:underline cursor-pointer">Back</a>
      </p>
    </div>
  </div>
</template>

<script>
import siteMetaInfo from "@/data/sitemetainfo";

export default {
  async asyncData({ params }){
    const resume = await fetch('https://raw.githubusercontent.com/lept-github/resume/master/luis-pacehco-resume.json').then(res => res.json());
    return { resume, job: resume.work.find(job => job.id === params.slug) };
  },
  methods: {
    back(){
      window.history.back()
    },
  },
  head: {
    title: siteMetaInfo.title,
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: siteMetaInfo.description,
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>
