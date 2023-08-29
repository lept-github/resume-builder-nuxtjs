<template>
  <div class="max-w-3xl px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0">
    <div class="pt-6 pb-8 space-y-2 md:space-y-5">
      <h1 class="text-3xl font-extrabold leading-9 tracking-tight text-gray-900 dark:text-gray-100 sm:text-4xl sm:leading-10 md:text-6xl md:leading-14">
        Blog
      </h1>
    </div>
    <div class="space-y-16 mx-auto max-w-7xl">
      <blog-item
        v-for="article in articles"
        :key="article.title"
        :title="article.title"
        :description="article.description"
        :date="article.date"
        :slug="article.slug"
      ></blog-item>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content("blog")
      .only([
        "title",
        "description",
        "img",
        "slug",
        "tag",
        "author",
        "date",
        "draft",
      ])
      .sortBy("date", "desc")
      .fetch();

    return {
      articles,
    };
  },
  head: {
    title: "Luis Pacheco | Blog",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: "This is Luis' Pen and Paper to write",
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>

<style></style>
