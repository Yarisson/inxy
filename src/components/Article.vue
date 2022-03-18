<template>
  <article class="article">
    <div class="article__img-wrapper">
      <img class="article__img" :src="getImg" alt="sport" />
    </div>
    <h3 class="article__title">{{ article.title }}</h3>

    <div class="article__info">
      <span class="article__info-date">{{ article.date }}</span>
      <span>{{ article.source }}</span>
    </div>

    <p class="article__text">{{ article.text }}</p>
    <a class="article__link" href="#">read more</a>
  </article>
</template>
<script>
export default {
  name: 'Article',
  props: ['article'],
  computed: {
    getImg() {
      if (!this.article.img) {
        return;
      }
      let FileName = this.article.img.toLowerCase();
      return require(`../assets/img/${FileName}.jpg`);
    },
  },
};
</script>

<style lang="scss">
@import '../sass/Article.scss';
</style>
