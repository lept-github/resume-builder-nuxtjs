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
      <Favorites :resume="resume" />
      <hr class="mb-0 mt-0 print:invisible" />
      <TimeLine :resume="resume" />
    </div>
  </div>
</template>

<script>
import siteMetaInfo from "@/data/sitemetainfo";
export default {
  async asyncData(){
    const resume = await fetch('https://raw.githubusercontent.com/lept-github/resume/master/luis-pacehco-resume.json').then(res => res.json());
    return { resume };
  },
  data() {
    return {
      siteMetaInfo: siteMetaInfo,
    };
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
