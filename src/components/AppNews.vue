<template>
  <div class="card">
    <h3>{{ news }}</h3>
    <button class="btn" @click="isOpen = !isOpen">
      {{ !isOpen ? "Раскрыть" : "Свернуть" }}
    </button>
    <p v-if="isOpen">Info...</p>
  </div>
  <br />
</template>

<script lang="ts">
export default {
  data() {
    return {
      isOpen: false,
    };
  },
  props: {
    news: {
      type: String, // Указываем тип свойства
      required: true, // Указали, что это свойство обязательно
    },
  },
};
</script>
