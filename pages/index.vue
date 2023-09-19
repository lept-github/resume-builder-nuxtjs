<template>
  <div class="max-w-screen-lg md:flex mx-auto">
    <div class="md:w-[325px]">
      <AuthorCard :resume="resume" />
    </div>
    <div class="md:w-2/3">
      <AuthorIntro :resume="resume" />
      <hr class="mb-0 mt-0" />
      <Skills :resume="resume" />
      <hr class="mb-0 mt-0" />
      <Tools :resume="resume" />
      <hr class="mb-0 mt-0 print:invisible" />
      <Journey :resume="resume" />
    </div>
  </div>
</template>

<script>
import siteMetaData from "@/data/siteMetaData";
import AuthorCard from "@/components/AuthorCard.vue";
import AuthorIntro from "@/components/AuthorIntro.vue";
import Skills from "@/components/Skills.vue";
import Tools from '@/components/Tools.vue';
import Journey from '@/components/Journey.vue';

export default {
  components: { AuthorCard, AuthorIntro, Skills, Tools, Journey },
  async asyncData(){
    const resume = await fetch('https://raw.githubusercontent.com/lept-github/resume/master/luis-pacehco-resume.json').then(res => res.json());
    return { resume };
  },
  head: {
    title: `${siteMetaData.title} - Home`,
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: siteMetaData.description,
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>
