<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Testimony from './components/Testimony.vue';
import json from "./assets/data.json"

const data = json
</script>

<template>
  <main class="main">
    <Testimony v-for="item in data" :class="item.color ? 'card--' + item.color : ''" :name="item.name" :status="item.status" :title="item.title" :content="item.content" :background="item.background" />
  </main>
</template>

<style scoped lang="scss">
  .main {
    padding: 1.5rem;
    gap: 1.5rem;
    display: grid;
  }

  @include breakpoint {
    .main {
      max-width: 1100px;
      grid-template-columns: repeat(4, 1fr);
      grid-template-rows: repeat(2, auto);
      & .card:first-child, & .card:nth-child(4) {
        grid-column: span 2;
      }
      & .card:last-child {
        grid-column: 4/5;
        grid-row: 1 / span 2;
      }
    }
  }
</style>
