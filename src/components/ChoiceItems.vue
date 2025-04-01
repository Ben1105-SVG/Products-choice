<template>
  <div>
    <div class="top-right">
      <h3>Selected Item (Choice)</h3>
      <div class="items-container">
        <div class="item" v-if="selectedChoiceItem">
          {{ selectedChoiceItem.name }}
        </div>
        <p v-else>No item selected</p>
      </div>
    </div>
    <div class="bottom-right">
      <h3>Choice Items</h3>
      <div class="items-container">
        <div
          v-for="item in choiceItems"
          :key="item.id"
          @click="selectChoiceItem(item)"
          :class="['item', { selected: selectedChoiceItem && selectedChoiceItem.id === item.id }]"
        >
          {{ item.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

    defineProps({
    choiceItems: Array,
    selectedChoiceItem: Object,
});

const emit = defineEmits(['select-choice-item']);

const selectChoiceItem = (item) => {
    emit('select-choice-item', item);
};
</script>
