<template>
  <div>
    <UiPageHeader
      :path="[{ label: 'VISIONS', to: '/visions/' }]"
      subject="VISIONS"
      subheading="VISIONS"
    />

    <div class="l-container--large l-container--contents">
      <article class="c-article">
        <header>
          <h1 class="c-heading--lv1">
            {{ response.details.subject }}
          </h1>
          <time class="c-topics__date" :datetime="response.details.ymd">{{
            response.details.ymd
          }}</time>
          <span class="c-badge">
            {{ response.details.area }}
          </span>
        </header>
        <div class="l-container--contents">
          <div v-html="response.details.contents"></div>
        </div>

        <hr />
        <div class="l-container--contents u-pt-30 u-text-align-center">
          <NuxtLink :to="'/visions/'" class="c-button">
            一覧へ戻る
          </NuxtLink>
        </div>
      </article>

    </div>
  </div>
</template>

<script setup>
const config = useRuntimeConfig();

// const { isLoggedIn } = useAuth();

const route = useRoute();
const response = await $fetch(
  `${config.public.kurocoApiDomain}/rcms-api/5/visions/details/${route.params.slug}`,
  {
    credentials: "include",
    server: false,
  }
).catch((error) => console.info(error));
</script>
