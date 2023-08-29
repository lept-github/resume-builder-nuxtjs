<template>
  <div class="md:fixed">
    <div class="flex justify-center print:hidden">
      <nuxt-img src="/avatar-02.png" loading="lazy" alt="me" class="md:h-60 md:w-60 h-20 w-20 rounded-full" />
    </div>
    <h1 class="mt-3 font-bold text-4xl text-sky-400 text-center">
      {{ resume.basics.name }}
    </h1>
    <h2 class="mt-3 text-lg text-gray-500 text-center">
      {{ resume.basics.label }}
    </h2>
    <p class="mt-3 mb-0 md:text-xs md:w-60 text-gray-400 text-center">
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
      <li class="mr-3">
        <a href="https://www.linkedin.com/in/lept/" class="flex items-center">
          <Linkedin /> <span class="hidden print:inline text-gray-400">Linkedin</span>
        </a>
      </li>
      <li class="mr-3">
        <a href="https://github.com/lept-github" class="flex items-center">
          <Github /> <span class="hidden print:inline text-gray-400">Github</span>
        </a>
      </li>
    </ul>
    <p class="mt-3 mb-0 md:text-xs md:w-60 text-gray-400 text-center print:invisible">
      Florida, US
    </p>
  </div>
</template>

<script>
import Phone from "../assets/icon/phone.svg?inline";
import Mail from "../assets/icon/mail.svg?inline";
import Glob from "../assets/icon/glob.svg?inline";
import Home from "../assets/icon/home.svg?inline";
import Github from "../assets/icon/github_new.svg?inline";
import Linkedin from "../assets/icon/linkeding.svg?inline";

export default {
  components: { Phone, Mail, Glob, Home, Github, Linkedin },
  props: {
    resume: Object
  }
};
</script>
