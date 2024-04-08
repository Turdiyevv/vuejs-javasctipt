
<script setup>
import { ref } from "vue";

const expanded = ref(false);
const childExpanded = ref(false);

function toggleExpand() {
  console.log()
  expanded.value = !expanded.value;
}

function toggleChildExpand() {
  console.log()
  childExpanded.value = !childExpanded.value;
}
</script>

<template>
  <div class="greetings">
    <ul>
      <li>
        <a class="expand" @click="toggleExpand">Root</a>
        <ul v-show="expanded">
          <li>
            <a class="expand" @click="toggleChildExpand">Child</a>
            <ul v-show="childExpanded">
              <li>
                <a class="expand">Super Child</a>
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.greetings{
  color: white;
}
ul li ul {
  display: none;
}
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
