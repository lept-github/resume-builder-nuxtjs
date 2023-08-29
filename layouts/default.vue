<template>
  <section class="w-full px-6 pb-12 antialiased bg-white">
    <div class="mx-auto max-w-8xl">
      <TheHeader />
      <Nuxt />
      <TheFooter />
    </div>
  </section>
</template>

<script>
import TheHeader from "../components/TheHeader.vue";
import TheFooter from "../components/TheFooter.vue";

export default {
  component: {
    TheHeader,
    TheFooter,
  },
  async asyncData(){
    const resume = await fetch('https://raw.githubusercontent.com/lept-github/resume/master/luis-pacehco-resume.json').then(res => res.json());
    return { resume };
  },
};
</script>
