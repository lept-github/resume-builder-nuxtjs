<template>
  <article>
    <div class="mb-6">
      <h4 class="mt-6 text-2xl text-gray-900 font-bold">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug } }">
          {{ title }}
        </NuxtLink>
      </h4>
      <time class="text-gray-400">{{ formatDate(date) }}</time>
    </div>
    <p>
      {{ description }}
      <NuxtLink class="text-sky-400 hover:underline" :to="{ name: 'blog-slug', params: { slug } }">
        More
      </NuxtLink>
    </p>
  </article>
</template>

<script>
export default {
  props: ["title", "description", "date", "slug"],
  data() {
    return {
      title: this.title,
      description: this.description,
      slug: this.slug,
      date: this.date,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>
