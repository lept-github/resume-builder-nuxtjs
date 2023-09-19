<template>
  <div class="mt-10 max-w-2xl mx-auto">
    <div class="mt-10 mb-6">
      <h1 class="text-6xl font-extrabold text-gray-900">
        Projects
      </h1>
    </div>
    <div class="flex flex-wrap -m-3">
      <ProjectCard
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
import projectsData from "@/data/projects";
import ProjectCard from "@/components/ProjectCard.vue";

export default {
  components: { ProjectCard },
  data() {
    return {
      projectsData: projectsData,
    };
  },
  head: {
    title: "Luis Pacheco - Projects",
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
