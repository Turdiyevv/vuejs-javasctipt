<script setup>

import {reactive} from "vue";

const props = defineProps(
    {
      treeData: Array,
      isVisible: Boolean,
    }
)
let treeItem = reactive({isActive: false});
const toggleItem = () => {
  treeItem.isActive = !treeItem.isActive;
}
</script>

<template>
  <ul class="my-tree" :class="isVisible ? 'd-block' : 'd-none'">
    <li v-for="item in treeData" :key="item.id">
      <h3 @click="toggleItem">{{ item.text }}</h3>
      <div v-if="item.child && item.child.length > 0">
        <tree :tree-data="item.child" :is-visible="treeItem.isActive" />
      </div>
    </li>
  </ul>
</template>
