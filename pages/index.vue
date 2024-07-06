<template>
  <div>
    <section class="c-hero">
      <div class="c-hero__body">
        <p class="c-hero__body__lead"><span>ビルに<br>駐車場に<br>動画広告を</span></p>
        <ul class="c-hero__body__buttons">
          <li class="c-hero__body__buttons__item">
            <NuxtLink to="/company/" @click.native="Drawer = false" class="c-button"
              >資料請求</NuxtLink
            >
          </li>
          <li class="c-hero__body__buttons__item">
            <NuxtLink to="/contact/" @click.native="Drawer = false" class="c-button"
              >お問い合わせ</NuxtLink
            >
          </li>
        </ul>
      </div>
      <img src="~/assets/image/building.png" alt="hero" class="c-hero__image" />
    </section>

    <section class="l-container--large l-container--contents">
      <div class="c-section--image-text">
        <div class="u-display-flex-grow-1">
            <h2 class="c-heading--sub">Steps</h2>
          <h2 class="c-heading--lv1">掲載までの流れ</h2>
          <ul class="c-flow">
            <li class="c-flow__item"><span>依頼</span></li>
            <li class="c-flow__item"><span>審査</span></li>
            <li class="c-flow__item"><span>配信</span></li>
          </ul>
          <p class="c-text">
            掲載までの流れについての簡単なアピール文章
          </p>
          <!-- <NuxtLink to="/service/" class="c-button">もっと詳しく</NuxtLink> -->
        </div>
      </div>
    </section>

    <!-- <section class="l-container--large l-container--contents">
      <div class="c-section--list">
        <div class="c-section--list__heading">
          <p class="c-heading--sub">News Release</p>
          <h2 class="c-heading--lv1">ニュースリリース</h2>
          <NuxtLink to="/news/" class="c-button">一覧を見る</NuxtLink>
        </div>

        <div class="u-display-flex-grow-1">
          <ul v-if="news.list.length > 0" class="c-topics-list">
            <li v-for="news in news.list" :key="news.topics_id">
              <NuxtLink :to="`/news/detail/${news.topics_id}`" class="c-topics">
                <time class="c-topics__date" :datetime="news.ymd">{{
                  news.ymd
                }}</time>
                <span class="c-badge">
                  {{ news.contents_type_nm }}
                </span>
                <p class="c-topics__title">
                  {{ news.subject }}
                </p>
              </NuxtLink>
            </li>
          </ul>
          <p v-else>記事が存在しません</p>
        </div>
      </div>
    </section> -->

    <section class="l-container--contents c-section--bg">
      <div class="l-container--large">
        <div class="u-display-flex u-display-flex-align-items-center u-mb-20">
          <div class="u-display-flex-grow-1">
            <p class="c-heading--sub">Visions</p>
            <h2 class="c-heading--lv1">Visions</h2>
          </div>
        </div>

        <UiCardList
          v-if="visions?.list?.length > 0"
          :list="visions.list"
        ></UiCardList>

        <div class="u-display-flex u-display-flex-align-items-center u-display-flex-justify-content-center u-mb-20">
          <div class="u-display-flex-shrink-0">
            <NuxtLink to="/ltd-news/" class="c-button"
              >read more</NuxtLink
            >
          </div>
        </div>

        <div class="l-container--contents">
          <div
            class="c-section--dark-block c-section--list u-display-flex-align-items-end"
          >
            <div class="c-section--list__heading">
              <p class="c-heading--sub">Prices</p>
              <h2 class="c-heading--lv1">掲載料金</h2>
            </div>
            <div class="c-section--dark-block-price u-display-flex-grow-1 u-display-flex-shrink-1">
              <b class="p1">@</b>
              <b class="p2">30</b>
              <b class="p3">円</b>
              <b class="p4">〜</b>
              <b class="p5">（50,000円/月〜）</b>
            </div>
          </div>
          <div>
            <p class="c-text c-text--small">
              ※ 放映時間15秒/回 放映頻度 4回/h （7〜24時）
              ※ 設置場所の視認性や通行量により金額は変動します
            </p>
          </div>
          <NuxtLink to="/login/register/" class="c-button c-button--full"
              >お問い合わせ</NuxtLink
            >
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const config = useRuntimeConfig();

const { data: news } = await useFetch(
  `${config.public.kurocoApiDomain}/rcms-api/1/news/list`,
  {
    credentials: "include",
    server: false,
  }
);
console.log({news});
const { data: visions } = await useFetch(
  `${config.public.kurocoApiDomain}/rcms-api/5/visions/list`,
  {
    credentials: "include",
    server: false,
  }
);
console.log({visions});
</script>
