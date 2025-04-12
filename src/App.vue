<template>
  <AppNews v-for="item of news" :key="item" :news="item" />
</template>

<style lang="scss">
@import "./styles/theme.scss";
</style>

<script lang="ts">
import AppNews from "./components/AppNews.vue";
export default {
  data() {
    return {
      news: [
        "Windows 12 is out",
        "Linux Kernel 2.1 is out",
        "Trump has made Elon Musk his son",
      ],
    };
  },
  components: {
    AppNews: AppNews,
  },
};
</script>
