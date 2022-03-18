<template>
  <header class="header">
    <nav class="nav">
      <a
        class="nav__link"
        :class="{ active: newsIsActive }"
        href=""
        @click="clearSearch"
        >News</a
      >
      <a class="nav__link" href="">Portal</a>
    </nav>

    <div class="header__search">
      <button
        v-show="isActiveSearch"
        class="header__search-clear"
        @click="clearSearch">
        <svg class="header__clear-icon"
          version="1.1"
          id="Capa_1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          x="0px"
          y="0px"
          width="94.926px"
          height="94.926px"
          viewBox="0 0 94.926 94.926"
          style="enable-background: new 0 0 94.926 94.926"
          xml:space="preserve">
          <g>
            <path
              d="M55.931,47.463L94.306,9.09c0.826-0.827,0.826-2.167,0-2.994L88.833,0.62C88.436,0.224,87.896,0,87.335,0
		c-0.562,0-1.101,0.224-1.498,0.62L47.463,38.994L9.089,0.62c-0.795-0.795-2.202-0.794-2.995,0L0.622,6.096
		c-0.827,0.827-0.827,2.167,0,2.994l38.374,38.373L0.622,85.836c-0.827,0.827-0.827,2.167,0,2.994l5.473,5.476
		c0.397,0.396,0.936,0.62,1.498,0.62s1.1-0.224,1.497-0.62l38.374-38.374l38.374,38.374c0.397,0.396,0.937,0.62,1.498,0.62
		s1.101-0.224,1.498-0.62l5.473-5.476c0.826-0.827,0.826-2.167,0-2.994L55.931,47.463z" />
          </g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
        </svg>
      </button>
      <input
        class="header__input"
        v-show="isActiveSearch"
        v-model="searchArticle"
        @keyup.enter="search"
        type="text" />

      <button
        class="header__button"
        v-show="!isActiveSearch"
        @click="startSearch">
        <svg
          width="22"
          height="21"
          viewBox="0 0 22 21"
          fill="none"
          xmlns="http://www.w3.org/2000/svg">
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M13.7434 4.54103C16.2807 7.00365 16.2807 10.9963 13.7434 13.459C11.2062 15.9216 7.09249 15.9216 4.55524 13.459C2.01799 10.9963 2.01799 7.00365 4.55524 4.54103C7.09249 2.07841 11.2062 2.07841 13.7434 4.54103ZM15.8529 14.1157C18.4908 10.8677 18.2661 6.14474 15.1786 3.14808C11.8487 -0.083843 6.44995 -0.083843 3.12008 3.14808C-0.209788 6.38001 -0.209788 11.62 3.12008 14.8519C6.20756 17.8486 11.0737 18.0667 14.4201 15.5063C14.4333 15.5206 14.4469 15.5347 14.4611 15.5484L19.2845 20.2299C19.6808 20.6146 20.3233 20.6146 20.7196 20.2299C21.1159 19.8453 21.1159 19.2216 20.7196 18.837L15.8962 14.1554C15.8821 14.1417 15.8676 14.1285 15.8529 14.1157Z"
            fill="#444444" />
        </svg>
      </button>
    </div>
  </header>
</template>
<script>
export default {
  name: 'Header',
  data: () => ({
    newsIsActive: true,
    isActiveSearch: false,
    searchArticle: '',
  }),
  methods: {
    startSearch() {
      return (this.isActiveSearch = true);
    },
    search() {
      this.isActiveSearch = !this.isActiveSearch;
      this.$emit('searchArticles', this.searchArticle);
      this.searchArticle = '';
    },
    clearSearch() {
      this.isActiveSearch = !this.isActiveSearch;
      this.$emit('searchArticles', '');
    },
  },
};
</script>

<style lang="scss">
@import '../sass/Header.scss';
</style>
