<template>
  <div class="l-container--wrap">
    <UiPageHeader subject="VISIONS" subheading="Visions" />
    <section>
      <div class="l-container--large">
        <div class="l-container--contents">
          <UiCardList
            v-if="visions?.list?.length > 0"
            :list="visions.list"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const config = useRuntimeConfig();
const { data: visions } = await useFetch(
  `${config.public.kurocoApiDomain}/rcms-api/5/visions/list`,
  {
    credentials: "include",
    server: false,
  }
);
</script>
