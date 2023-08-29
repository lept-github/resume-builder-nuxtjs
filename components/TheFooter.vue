<template>
  <footer>
    <div class="flex flex-col items-center mt-20">
      <div class="flex space-x-4">
        <a target="_blank" rel="noopener noreferrer" :href="`mailto:${siteMetadata.email}`">
          <img class="w-8 h-8" src="~assets/icon/mail.svg" />
        </a>
        <a target="_blank" rel="noopener noreferrer" :href="siteMetadata.linkedin">
          <img class="w-8 h-8" src="~assets/icon/linkeding.svg" />
        </a>
        <a target="_blank" rel="noopener noreferrer" :href="siteMetadata.github">
          <img class="w-8 h-8" src="~assets/icon/github_new.svg" />
        </a>
      </div>
      <p class="text-base font-normal text-gray-500 dark:text-gray-400">
        <span>Copyright ©{{ new Date().getFullYear() }}</span>
        <span>•</span>
        <span>{{ siteMetadata.author }}</span>
      </p>
    </div>
  </footer>
</template>

<script>
import siteMetaInfo from "@/data/sitemetainfo";
import BuyMeACoffee from "./BuyMeACoffee.vue";
export default {
  data() {
    return {
      siteMetadata: siteMetaInfo,
    };
  },
  components: { BuyMeACoffee },
};
</script>
