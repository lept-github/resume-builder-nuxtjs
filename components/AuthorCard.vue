<template>
  <div class="md:fixed">
    <div class="flex justify-center print:hidden">
      <nuxt-img :src="siteMetaData.author_image" loading="lazy" :alt="resume.basics.name" class="md:h-60 md:w-60 h-20 w-20 rounded-full" />
    </div>
    <h1 class="mt-3 font-bold text-4xl text-sky-400 text-center">
      {{ resume.basics.name }}
    </h1>
    <h2 class="mt-3 text-lg text-gray-500 text-center">
      {{ resume.basics.label }}
    </h2>
    <p class="mt-3 mb-0 md:text-xs md:w-60 text-gray-400 text-center print:hidden">
      {{ resume.basics.motto }}
    </p>
    <ul class="mt-3 mb-0 flex items-center justify-center">
      <li class="mr-3">
        <a :href="`https://www.${ resume.basics.url }`" class="flex items-center">
          <Home /> <span class="hidden print:inline text-gray-400">{{ resume.basics.url }}</span>
        </a>
      </li>
      <li class="mr-3">
        <a :href="`tel:${ resume.basics.phone }`" class="flex items-center">
          <Phone /> <span class="hidden print:inline text-gray-400 ml-1">{{ resume.basics.phone }}</span>
        </a>
      </li>
      <li class="mr-3">
        <a :href="`mailto:${ resume.basics.email }`" class="flex items-center">
          <Mail /> <span class="hidden print:inline text-gray-400">{{ resume.basics.email }}</span>
        </a>
      </li>
      <li v-for="profile in resume.basics.profiles" :key="profile.network" class="mr-3">
        <a :href="profile.url" class="flex items-center">
          <Linkedin v-if="profile.network === 'linkedin'" />
          <Github v-if="profile.network === 'github'" />
          <span class="hidden print:inline text-gray-400">{{ profile.username }}</span>
        </a>
      </li>
    </ul>
    <p class="mt-3 mb-0 md:text-xs md:w-60 text-gray-400 text-center print:invisible">
      {{ siteMetaData.location }}
    </p>
  </div>
</template>

<script>
import siteMetaData from "@/data/siteMetaData";
import Phone from "../assets/icon/phone.svg?inline";
import Mail from "../assets/icon/mail.svg?inline";
import Glob from "../assets/icon/glob.svg?inline";
import Home from "../assets/icon/home.svg?inline";
import Github from "../assets/icon/github_new.svg?inline";
import Linkedin from "../assets/icon/linkeding.svg?inline";

export default {
  data() {
    return {
      siteMetaData
    };
  },
  components: { Phone, Mail, Glob, Home, Github, Linkedin },
  props: {
    resume: Object
  }
};
</script>
