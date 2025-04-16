<template>
  <div class="card">
    <h3>{{ news.title }}</h3>
    <button class="btn" @click="toggleItem">
      {{ !isOpen ? "Раскрыть" : "Свернуть" }}
    </button>

    <div v-if="isOpen">
      <p>Info...</p>
      <button
        class="btn"
        :class="!news.read ? 'primary' : ''"
        @click="readTheArticle"
      >
        {{ news.read ? "Прочитано" : "Прчитать" }}
      </button>
    </div>
  </div>
  <br />
</template>

<script>
export default {
  emits: ["read", "item-opened"],
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    readTheArticle() {
      this.$emit("read");
    },
    toggleItem() {
      this.isOpen = !this.isOpen;
      if (this.isOpen) this.$emit("item-opened", true);
    },
  },
  props: {
    news: {
      type: String, // Указываем тип свойства
      required: true, // Указали, что это свойство обязательно
    },
  },
};
</script>
