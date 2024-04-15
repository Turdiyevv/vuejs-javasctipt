
<script setup>
import {computed, ref, watch} from "vue";
const props = defineProps(
    {treeData: Array}
)

const expanded = ref([]);
const toggleExpand = (id) => {
  if (expanded.value.includes(id)) {
    expanded.value = expanded.value.filter(itemId => itemId !== id);
  } else {
    expanded.value.push(id);
  }
};

const watchedTreeData = computed(() => {
  expanded.value = props.treeData.map(item => item.id);
  return props.treeData;
});
</script>

<template>
  <div class="greetings">
    <div v-for="item in treeData" :key="item.id">
      <div class="tree__class" @click="toggleExpand(item.id)">
        <div style="margin: 0 5px">{{item.id}}</div>
        <div>{{ item.text }}</div>
      </div>

        <div v-show="expanded.includes(item.id)"
             v-for="itemCh in item.child" :key="itemCh.id">
          <div class="tree__class-ch" @click="itemCh.child? toggleExpand(item.id) : ''">
            <div style="margin: 0 5px">{{itemCh.id}}</div>
            <div>{{ itemCh.text }}</div>
          </div>
<!--          <div class="tree__class-ch" v-if="itemCh.child">{{ itemCh.child }}</div>-->
        </div>

    </div>
  </div>
</template>

<style scoped>
.tree__class{
  margin: 2px;
  background-color: cornsilk;
}
.tree__class-ch{
  margin: 2px 2px 2px 32px;
  background-color: #7ef6f6;
}
.tree__class, .tree__class-ch{
  width: 130px;
  display: flex;
  cursor: pointer;
  padding: 10px;
  border-radius: 5px;
}
.tree__class:active{
  background-color: #faf7ee;
}
.tree__class-ch:active{
  background-color: #7EF6F6FF;
}
.greetings{
  color: blue;
}
</style>
