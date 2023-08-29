<template>
  <div class="mt-10">
    <h2 class="mt-6 text-4xl text-gray-900 font-bold">
      Hello There<span class="text-sky-400">!</span>
    </h2>
    <p class="mt-6 mb-9 text-gray-500 text-justify">
      {{ resume.basics.summary2 }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    resume: Object
  }
};
</script>
