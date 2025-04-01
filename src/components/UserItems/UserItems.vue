<template>
  <div>
    <div class="top-left">
      <h3>Selected Items (User)</h3>
      <div class="items-container">
        <div v-for="item in selectedUserItems" :key="item.id" class="item">
          {{ item.name }}
        </div>
      </div>
    </div>
    <div class="bottom-left">
      <h3>User Items</h3>
      <div class="items-container">
        <div
          v-for="item in userItems"
          :key="item.id"
          @click="toggleUserItem(item)"
          :class="['item', { selected: selectedUserItems.includes(item) }]"
        >
          {{ item.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  userItems: Array,
    selectedUserItems: Array,
});
const emit = defineEmits(['toggle-user-item']);

const toggleUserItem = (item) => {
  emit("toggle-user-item", item);
}
</script>

<style scoped>
@import './UserItems.css';
</style>