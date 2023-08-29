<template>
  <div class="max-w-3xl px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0">
    <div class="pt-6 pb-8 space-y-2 md:space-y-5">
      <h1 class="text-3xl font-extrabold leading-9 tracking-tight text-gray-900 dark:text-gray-100 sm:text-4xl sm:leading-10 md:text-6xl md:leading-14">
        News
      </h1>
    </div>
    <div class="space-y-16 mx-auto max-w-7xl">
      tbd
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles")
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
      .sortBy("date", "asc")
      .fetch();

    return {
      articles,
    };
  },
  head: {
    title: "Luis Pacheco | News",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: "Latest tech news from around the world and the interwebz",
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>

<style></style>
