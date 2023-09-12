<template>
  <div class="mt-10 max-w-2xl mx-auto">
    <div class="mt-10 mb-6">
      <h1 class="text-6xl font-extrabold text-gray-900">
        Blog
      </h1>
    </div>
    <Article
      v-for="article in articles"
      :key="article.title"
      :title="article.title"
      :description="article.description"
      :date="article.date"
      :slug="article.slug"
    ></Article>
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
      .where({ draft: false })
      .sortBy("date", "desc")
      .fetch();

    return { articles };
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
