<template>
  <div class="px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0 mt-10">
    <p class="text-center font-bold my-5 text-indigo-500">
      {{ formatDate(article.date) }}
    </p>
    <h1 class="text-4xl text-gray-700 font-extrabold mb-10 text-center">
      {{ article.title }}
    </h1>
    <div class="flex items-center font-medium mt-6 sm:mx-3 justify-center">
      <nuxt-img :src="siteMetaData.author_image" loading="lazy" alt="" class="mr-3 w-10 h-10 rounded-full bg-slate-50 dark:bg-slate-800" />
      <div>
        <div class="text-slate-900 dark:text-slate-200">
          {{ siteMetaData.author }}
        </div>
        <a target="_blank" :href="siteMetaData.twitter" class="text-sky-500 hover:text-sky-600 dark:text-sky-400">
          @{{ siteMetaData.twitter_user }}
        </a>
      </div>
    </div>
    <img class="mx-auto w-4/5 my-10 rounded-md drop-shadow-sm" :src="article.image" />
    <nuxt-content class="prose min-w-full p-10 mx-auto" :document="article" />
  </div>
</template>

<script>
import Prism from "~/plugins/prism";
import siteMetaData from "@/data/siteMetaData";

export default {
  data() {
    return {
      siteMetaData,
    };
  },
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug).fetch();
    return {
      article: article,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
  mounted() {
    Prism.highlightAll();
  },
  head: {
    title: siteMetaData.title,
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