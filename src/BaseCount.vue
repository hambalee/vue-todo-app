<script setup lang="ts">
import { ref, computed } from "vue";

const name = ref("Lee");
const count = ref(0);

const onIncrement = () => {
  count.value++;
};

const onDecrement = () => {
  count.value--;
};

const countText = computed(() => `Count: ${count.value}`);
</script>

<template>
  <h1>My name is {{ name }}.</h1>
  <div class="count-text">{{ countText }}</div>
  <!-- Directive -->
  <div v-if="count % 2 == 1" class="count-text">is odd</div>
  <div v-else-if="count == 0" class="count-text">is zero</div>
  <div v-else class="count-text">is even</div>
  <button class="count-button" @click="onIncrement()">+</button>
  <button class="count-button" @click="onDecrement()">-</button>
</template>

<style scoped>
.count-button {
  padding: 16px;
  margin: 16px;
}

.count-text {
  font-size: 32px;
}
</style>
