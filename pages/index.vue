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
          v-if="ltdNews?.data?.list?.length > 0"
          :list="ltdNews.data.list"
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
// const { data: ltdNews } = await useFetch(
//   `${config.public.kurocoApiDomain}/rcms-api/1/ltd-news/list`,
//   {
//     credentials: "include",
//     server: false,
//   }
// );
const ltdNews = {
  "errors": [],
  "messages": [],
  "data": {
      "list": [
          {
              "topics_id": 8,
              "ymd": "2023-08-09",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "8_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00001.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/8_ext_1_0.png"
              }
          },
          {
              "topics_id": 9,
              "ymd": "2023-06-26",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "9_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00002.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/9_ext_1_0.png"
              }
          },
          {
              "topics_id": 10,
              "ymd": "2022-12-20",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "10_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00003.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/10_ext_1_0.png"
              }
          },
          {
              "topics_id": 11,
              "ymd": "2023-08-09",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "8_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00001.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/8_ext_1_0.png"
              }
          },
          {
              "topics_id": 12,
              "ymd": "2023-06-26",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "9_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00002.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/9_ext_1_0.png"
              }
          },
          {
              "topics_id": 13,
              "ymd": "2022-12-20",
              "subject": "NBB BUILDING 屋上サイン",
              "contents_type_nm": "東京都渋谷区",
              "ext_1": {
                  "id": "10_ext_01_0",
                  "url": "https://daimonpei.g.kuroco-img.app/files/user/assets/images/v00003.png",
                  "desc": "",
                  "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/10_ext_1_0.png"
              }
          }
      ]
  }
};
console.log({ltdNews});
/*
{
    "ltdNews": {
        "__v_isShallow": false,
        "dep": {
            "w": 0,
            "n": 0
        },
        "__v_isRef": true,
        "_rawValue": {
            "errors": [],
            "messages": [],
            "data": {
                "list": [
                    {
                        "topics_id": 8,
                        "ymd": "2023-08-09",
                        "subject": "オンラインセミナーの動画配信",
                        "contents_type_nm": "プレミアム会員限定",
                        "ext_1": {
                            "id": "8_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/t=6e36e33863205d50cbf57eb3491caffd87c7e132c41bc42951a9ec29bed3671d/files/topics/8_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/8_ext_1_0.png"
                        }
                    },
                    {
                        "topics_id": 9,
                        "ymd": "2023-06-26",
                        "subject": "各種資料ダウンロード",
                        "contents_type_nm": "会員限定",
                        "ext_1": {
                            "id": "9_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/t=bd50490b3156207ad2d453bd747318e505b993dea904f9fdabc9c30570eb9855/files/topics/9_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/9_ext_1_0.png"
                        }
                    },
                    {
                        "topics_id": 10,
                        "ymd": "2022-12-20",
                        "subject": "ヘッドレスCMSと構築方法とは？",
                        "contents_type_nm": "誰でも閲覧可能",
                        "ext_1": {
                            "id": "10_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/v=1693802883/files/topics/10_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/10_ext_1_0.png"
                        }
                    }
                ]
            }
        },
        "_value": {
            "errors": [],
            "messages": [],
            "data": {
                "list": [
                    {
                        "topics_id": 8,
                        "ymd": "2023-08-09",
                        "subject": "オンラインセミナーの動画配信",
                        "contents_type_nm": "プレミアム会員限定",
                        "ext_1": {
                            "id": "8_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/t=6e36e33863205d50cbf57eb3491caffd87c7e132c41bc42951a9ec29bed3671d/files/topics/8_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/8_ext_1_0.png"
                        }
                    },
                    {
                        "topics_id": 9,
                        "ymd": "2023-06-26",
                        "subject": "各種資料ダウンロード",
                        "contents_type_nm": "会員限定",
                        "ext_1": {
                            "id": "9_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/t=bd50490b3156207ad2d453bd747318e505b993dea904f9fdabc9c30570eb9855/files/topics/9_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/9_ext_1_0.png"
                        }
                    },
                    {
                        "topics_id": 10,
                        "ymd": "2022-12-20",
                        "subject": "ヘッドレスCMSと構築方法とは？",
                        "contents_type_nm": "誰でも閲覧可能",
                        "ext_1": {
                            "id": "10_ext_01_0",
                            "url": "https://dev-nuxt-corporate.g.kuroco-img.app/v=1693802883/files/topics/10_ext_1_0.png",
                            "desc": "",
                            "url_org": "https://dev-nuxt-corporate.g.kuroco-img.app/files/topics/10_ext_1_0.png"
                        }
                    }
                ]
            }
        }
    }
}
*/
</script>
