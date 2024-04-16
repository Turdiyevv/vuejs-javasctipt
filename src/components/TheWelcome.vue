<script setup>
import {reactive, ref} from "vue";

const tableProps = defineProps(
    {table: Array}
)
const tableTh = reactive(tableProps.table[0]);
let tableTd = reactive(tableProps.table[1]);

let inputView = ref(false);
let val1 = ref('');
let val2 = ref('');
let val3 = ref('');
let val4 = ref('');
let currentItem = ref(null);

function editFunction(item){
    inputView.value = true;
    val1.value = item.text;
    val2.value = item.surname;
    val3.value = item.age;
    val4.value = item.id;
}
function update(val1,val2,val3){
  if (currentItem) {
    currentItem.text = val1;
    currentItem.surname = val2;
    currentItem.age = val3;
    currentItem.id = val4;
  }
    currentItem = tableTd.find(obj => obj.id === currentItem.id);
  inputView.value = false;
}
</script>

<template>
  <div style="color: white">
    <table>
      <tr v-for="item in tableTh" :key="item.id">
        <th>{{ item.text }}</th>
        <th>{{ item.text2 }}</th>
        <th>{{ item.text3 }}</th>
      </tr>
      <tr v-for="item in tableTd" :key="item.id">
        <td>{{item.text}}</td>
        <td>{{item.surname}}</td>
        <td>
          <span>{{item.age}}</span>
          <button @click="editFunction(item)" class="btn__style">+</button>
        </td>
      </tr>
    </table>
      <div v-show="inputView">
        <input v-model="val1" class="width__style">
        <input v-model="val2" class="width__style">
        <input v-model="val3" class="width__style">
        <button class="btn__style" @click="update(val1,val2,val3)">update</button>
      </div>

  </div>
</template>

<style scoped>
.btn__style{
  cursor: pointer;
  margin: 0 1px;
}
table{
    border-collapse: collapse;
    width: 100%;
}
td, th {
  text-align: left;
  padding: 8px;
}
.width__style{
  margin: 2px 6px;
}
</style>
