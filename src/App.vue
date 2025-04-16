<template>
  <div>
    <div class="card">
      <h3>Мои новости</h3>
      <hr />
      <h4>Вы посмотрели {{ views }} статей</h4>
      <h4>Вы прочитали {{ reads }} статей</h4>
    </div>
    <br />
    <AppNews
      v-for="item of news"
      :key="item"
      :news="item"
      @item-opened="this.views++"
      @read="item.read = true"
    />
  </div>
</template>

<style lang="scss">
@import "./styles/theme.scss";
</style>

<script>
import AppNews from "./components/AppNews.vue";
export default {
  data() {
    return {
      views: 0,
      news: [
        { title: "Windows 12 is out", read: false },
        { title: "Linux Kernel 2.1 is out", read: false },
        { title: "Trump has made Elon Musk his son", read: false },
      ],
    };
  },
  computed: {
    reads() {
      return this.news.reduce((total, item) => (total += item.read), 0);
    },
  },
  components: {
    AppNews: AppNews,
  },
};
</script>
