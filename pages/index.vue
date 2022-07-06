<script setup>
const { data: blogs } = await useAsyncData("blog", () =>
  queryContent("/blog").sort({ createdAt: 0 }).find()
);

const date = (value) =>
  new Date(value).toLocaleDateString("en-us", {
    month: "long",
    day: "numeric",
    year: "numeric",
  });
</script>

<template>
  <main>
    <Head>
      <Title>Jeroen Theunissen | Home Page</Title>
      <Meta
        name="description"
        content="Jeroen Theunissen Home Page, all Blogs about Vue.js, Nuxt, Supabase, JavaScript, TypeScript"
      />
    </Head>
    <div>
      <div
        v-for="blog in blogs"
        :key="blog.id"
        class="text-gray-700 dark:text-gray-200 border border-gray-200 rounded p-2 mb-4 hover:shadow-xl dark:hover:bg-gray-700 dark:border-gray-600 Class Properties transition-none transition-property: none; transition-all duration-500 ease-in-out"
      >
        <NuxtLink :to="blog._path">
          <div class="grid grid-cols-12 items-center">
            <div class="col-start-1 col-span-9">
              <h1 class="md:text-2xl text-xl p-1 font-bold">
                {{ blog.title }}
              </h1>
              <p class="md:text-lg p-1">{{ blog.description }}</p>
            </div>
            <div class="col-start-10 col-span-3 self-center justify-self-end">
              <img :src="blog.introImage" class="w-20 h-20" />
            </div>
          </div>
          <div
            class="text-gray-500 flex items-center justify-center py-1 border-t w-full border-gray-200 dark:border-gray-500"
          >
            <p class="text-italic text-brand-green-1 text-sm p-1">
              {{ blog.category }}
            </p>
            |
            <p class="text-italic text-sm p-2">
              {{ date(blog.createdAt) }}
            </p>
            |
            <p class="text-italic text-sm p-2 hover:cursor-pointer">
              Read more...
            </p>
          </div>
        </NuxtLink>
      </div>
    </div>
  </main>
</template>
