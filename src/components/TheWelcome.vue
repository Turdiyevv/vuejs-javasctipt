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
let val3 = ref(null);
let val4 = ref(null);

let currentItem = reactive({});

function editFunction(item){
    console.log(item);
    val4.value = item.id;
    val1.value = item.text;
    val2.value= item.surname;
    val3.value = item.age;
    inputView.value = true;
}

function update() {
  let itemIndex = tableTd.find(x => x.id === val4.value);
  if (itemIndex){
    itemIndex.text = val1.value;
    itemIndex.surname = val2.value;
    itemIndex.age = val3.value;
    console.log(itemIndex);
  }
    inputView.value = false;
  clear();
}

function clear(){
    val4.value = null;
    val1.value = '';
    val2.value= '';
    val3.value = null;
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
        <button class="btn__style" @click="update(currentItem)">update</button>
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
