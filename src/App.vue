<script setup>
import { ref } from 'vue';
import UserItems from './components/UserItems/UserItems.vue';
import ChoiceItems from './components/ChoiceItems/ChoiceItems.vue';
const userItems = ref([
      { id: 1, name: "Shoes 1" },
      { id: 2, name: "Shoes 2" },
      { id: 3, name: "Shoes 3" },
      { id: 4, name: "Shoes 4" },
      { id: 5, name: "T-shirt 1" },
      { id: 6, name: "T-shirt 2" },
      { id: 7, name: "T-shirt 3" },
      { id: 8, name: "T-shirt 4" },
    ]);

    const choiceItems = ref([
      { id: 11, name: "Jacket 1" },
      { id: 12, name: "Jacket 2" },
      { id: 13, name: "Jacket 3" },
      { id: 14, name: "Jacket 4" },
      { id: 15, name: "Hoodie 1" },
      { id: 16, name: "Hoodie 2" },
      { id: 17, name: "Hoodie 3" },
      { id: 18, name: "Hoodie 4" },
    ]);

    const selectedUserItems = ref([]);
    const selectedChoiceItem = ref(null);

    const toggleUserItem = (item) => {
      const index = selectedUserItems.value.indexOf(item);
      if (index > -1) {
        selectedUserItems.value.splice(index, 1);
      } else if (selectedUserItems.value.length < 6) {
        selectedUserItems.value.push(item);
      }
    };

    const selectChoiceItem = (item) => {
      selectedChoiceItem.value = item;
    };
</script>

<template>
  <main>
    <div class="container">
      <div class="grid">
        <UserItems
          :userItems="userItems"
          :selectedUserItems="selectedUserItems"
          @toggle-user-item="toggleUserItem"
        />
        <ChoiceItems
          :choiceItems="choiceItems"
          :selectedChoiceItem="selectedChoiceItem"
          @select-choice-item="selectChoiceItem"
        />
      </div>
    </div>
  </main>
</template>
