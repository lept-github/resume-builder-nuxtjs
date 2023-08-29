<template>
  <div class="max-w-3xl px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0">
    <div class="pt-6 pb-8 space-y-2 md:space-y-5">
      <h1 class="text-3xl font-extrabold leading-9 tracking-tight text-gray-900 dark:text-gray-100 sm:text-4xl sm:leading-10 md:text-6xl md:leading-14">
        Projects
      </h1>
    </div>
    <div class="flex flex-wrap -m-3">
      <project-card
        v-for="item in projectsData"
        :key="item.title"
        :title="item.title"
        :description="item.description"
        :href="item.href"
        :github="item.github"
        :tech1="item.tech1"
        :tech2="item.tech2"
        :tech3="item.tech3"
      />
    </div>
  </div>
</template>

<script>
import projectsData from "../../data/projects";
export default {
  data() {
    return {
      projectsData: projectsData,
    };
  },
  head: {
    title: "Luis Pacheco | Projects",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: "Some of the projects developed by Luis Pacheco",
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>
