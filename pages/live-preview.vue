<script setup lang="ts">
const { data: page } = await useAsyncData("live-preview", () =>
  queryContent("/live-preview").findOne(),
);

if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Page not found",
    fatal: true,
  });
}

useSeoMeta({
  title: page.value.title,
  ogTitle: `${page.value.title} – Kirby Tools`,
  description: page.value.description,
  ogDescription: page.value.description,
  ogImage: "https://kirby.tools/social-card-live-preview.png",
  twitterImage: "https://kirby.tools/social-card-live-preview.png",
});
</script>

<template>
  <LandingPage :page="page">
    <template #image-pricing>
      <IllustrationPartnershapes8 class="mx-auto w-3/4 md:w-4/5" />
    </template>
    <template #image-cta>
      <IllustrationPartnershapes20 class="mx-auto w-3/4" />
    </template>
  </LandingPage>
</template>
