<script setup>
import TreeMenuItem from "./TreeMenuItem.vue";

const props = defineProps({
  data: Array,
});
</script>
<template>
  <div v-for="item in data" :key="item.label" class="mt-2 px-2">
    <TreeMenuItem :item="item"></TreeMenuItem>
  </div>
</template>
