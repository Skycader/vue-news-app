<template>
  <div class="card">
    <h3>{{ item.title }}</h3>
    <button class="btn" :class="!isOpen ? 'primary' : ''" @click="toggleItem">
      {{ !isOpen ? "Раскрыть" : "Свернуть" }}
    </button>

    <div v-if="isOpen">
      <p>Info...</p>
      <br />
      <hr />
      <p>Читайте также</p>
      <p v-for="subitem of news" :key="subitem.id">
        <a href="https://gogol.com">{{ subitem.title }}</a>
      </p>
      <button
        class="btn"
        :class="!item.read ? 'primary' : ''"
        @click="readTheArticle"
      >
        {{ item.read ? "Прочитано" : "Прочитать" }}
      </button>
    </div>
  </div>
  <br />
</template>

<script>
export default {
  inject: ["title", "news"],
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
    item: {
      type: Object, // Указываем тип свойства
      required: true, // Указали, что это свойство обязательно
    },
  },
};
</script>
