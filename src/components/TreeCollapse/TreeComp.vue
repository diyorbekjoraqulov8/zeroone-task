<template>
  <ul class="w-max min-w-[200px]">
    <tree-node :data="item" v-for="item in data" :key="item.label"></tree-node>
  </ul>
</template>

<script setup>
import { toRefs } from "vue";
import TreeNode from "./TreeNode.vue";

const props = defineProps({
  data: Array, // Tree ma'lumotlarini olish uchun prop
})
const { data } = toRefs(props)
</script>