<template>
  <section class="page">
    <Header v-model:articles="articles" />
    <main class="page__main">
      <div class="page__title-wrapper">
        <h1 class="page__title">Latest News</h1>
        <div class="page__date-wrapper">
          <p class="page__date">
            <span class="page__date-day">Friday, </span>December 12, 2022
          </p>
          <button
            class="page__sort"
            :class="{ active: isBack }"
            @click="sortArticles">
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg">
              <path
                d="M3 7H21"
                stroke="#292D32"
                stroke-width="1.5"
                stroke-linecap="round" />
              <path
                d="M6 12H18"
                stroke="#292D32"
                stroke-width="1.5"
                stroke-linecap="round" />
              <path
                d="M10 17H14"
                stroke="#292D32"
                stroke-width="1.5"
                stroke-linecap="round" />
            </svg>
          </button>
        </div>
      </div>

      <section class="page__article-list">
        <Article v-for="item of articles" :key="item" :article="item" />
      </section>
    </main>
    <Footer />
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Article from './Article.vue';
import Footer from './Footer.vue';
import Header from './Header.vue';
import { ArticlesData } from '../data/ArticlesData';
import IArticle from '../ts/IArticle';

export default defineComponent({
  name: 'Main',
  components: {
    Article,
    Footer,
    Header,
  },
  data: () => ({
    isBack: false,
    articles: [] as IArticle[],
  }),
  created() {
    this.articles = ArticlesData;
  },
  methods: {
    sortArticles() {
      this.isBack = !this.isBack;
      if (this.isBack) {
        return this.articles.sort(
          (a, b) => Date.parse(a.date) - Date.parse(b.date)
        );
      } else {
        return this.articles.sort(
          (a, b) => Date.parse(b.date) - Date.parse(a.date)
        );
      }
    },
  },
});
</script>

<style lang="scss">
@import '../sass/Page.scss';
</style>
