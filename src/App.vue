<script setup>
import TheWelcome from './components/TheWelcome.vue'
import Tree from "@/components/tree.vue";
import {reactive} from "vue";

const treeData = [
  {
    id:0,
    text: 'Parent tree',
    child: [
      {id: 0, text: 'child1'},
      {id: 1, text: 'child1'}
    ]
  },
  {
    id:1,
    text: 'Parent2 tree',
    child: [
      {id: 0, text: 'child2'},
      {
        id: 1,
        text: 'child2',
        child: [
          {id: 0, text: 'child22'},
          {
            id: 1,
            text: 'child22',
            child: [
              {
                id: 1,
                text: "ututorejnfdkf",
                child: [
                  {
                    id: 1,
                    text: "ututorejnfdkfsdsd",
                    child: [

                    ],
                  }
                ],
              }
            ],
          }
        ]
      }
    ]
  },
  {
    id:2,
    text: 'Parent3 tree',
    child: [
      {id: 0, text: 'child3'},
      {id: 1, text: 'child3'}
    ],
  },
]

const table = reactive([
    [
      {id: 0, text: 'name', text2: 'surname', text3: 'age'},
    ],
    [
      {id: 1, text: 'name1', surname:'awd', age: 0},
      {id: 2, text: 'name22', surname:'jump', age: 0},
      {id: 3, text: 'name33', surname:'upg', age: 0}
    ]
])
</script>

<template>
  <header style="border: 1px solid red">

    <div class="wrapper">
      <tree :tree-data="treeData" :is-visible="true" />
    </div>
  </header>

  <main style="border: 1px solid red">
    <TheWelcome :table="table" />
  </main>
</template>

<style>
.my-tree{
  color: white;
}
.d-block {
  display: block;
}
.d-none {
  display: none;
}
</style>
