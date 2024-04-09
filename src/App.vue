<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

const treeData = [
  {
    id:0, text: 'Parent tree', child: [
      {id: 0, text: 'child1'},
      {id: 1, text: 'child1'}
    ]
  },
  {
    id:1, text: 'Parent2 tree', child: [
      {id: 0, text: 'child2'},
      {id: 1, text: 'child2', child: [
          {id: 0, text: 'child22'},
          {id: 1, text: 'child22'}
        ]
      }
    ]
  },
  {
    id:2, text: 'Parent3 tree', child: [
      {id: 0, text: 'child3'},
      {id: 1, text: 'child3'}
    ]
  },
]

const table = [
    [
      {id: 0, text: 'name', text2: 'surname', text3: 'age'},
    ],
    [
      {id: 0, text: 'name1', surname:'awd', age: '21'},
      {id: 1, text: 'name22', surname:'aedwedwed', age: '31'},
      {id: 2, text: 'name33', surname:'seddds', age: '15'}
    ]
]
</script>

<template>
  <header style="border: 1px solid red">

    <div class="wrapper">
      <HelloWorld :treeData="treeData" />
    </div>
  </header>

  <main style="border: 1px solid red">
    <TheWelcome :table="table" />
  </main>
</template>

<style scoped>
</style>
