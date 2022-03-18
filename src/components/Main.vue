<template>
  <section class="page">
    <Header @search-articles="searchArticles" />
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
        <Article v-for="item of filteredList" :key="item" :article="item" />
      </section>
    </main>
    <Footer />
  </section>
</template>

<script>
import Article from './Article.vue';
import Footer from './Footer.vue';
import Header from './Header.vue';

export default {
  name: 'Main',
  components: {
    Article,
    Footer,
    Header,
  },
  data: () => ({
    articleList: [
      {
        img: 'image1',
        text: 'Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis.',
        title: 'Some news',
        date: '12.12.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image2',
        text: 'Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... ',
        title: 'News of the world',
        date: '12.11.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image3',
        text: 'Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.',
        title: 'Origal news',
        date: '12.11.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image4',
        text: 'Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis.',
        title: 'Some some text about nothing',
        date: '12.03.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image5',
        text: 'Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis.',
        title: 'News Title Lorem Ipsum Dolor Sit Amet',
        date: '12.26.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image6',
        text: 'Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... ',
        title: 'News Title Lorem Ipsum Dolor Sit Amet',
        date: '11.11.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image7',
        text: 'Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.',
        title: 'News Title Lorem Ipsum Dolor Sit Amet',
        date: '12.15.2021',
        source: 'CNN Indonesia',
      },
      {
        img: 'image8',
        text: 'Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.',
        title: 'News Title Lorem Ipsum Dolor Sit Amet',
        date: '12.06.2021',
        source: 'CNN Indonesia',
      },
    ],
    isBack: false,
    filteredList: [],
  }),
  mounted() {
    this.filteredList = this.articleList;
  },
  methods: {
    sortArticles() {
      this.isBack = !this.isBack;
      if (this.isBack) {
        return this.filteredList.sort(
          (a, b) => Date.parse(a.date) - Date.parse(b.date)
        );
      } else {
        return this.filteredList.sort(
          (a, b) => Date.parse(b.date) - Date.parse(a.date)
        );
      }
    },
    searchArticles(article) {
      this.filteredList = this.articleList.filter((el) => {
        return el.title.toLowerCase().includes(article.toLowerCase());
      });
    },
  },
};
</script>

<style lang="scss">
@import '../sass/Page.scss';
</style>
