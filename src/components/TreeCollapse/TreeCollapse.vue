<template>
  <tree-node :data="item" v-for="item in data" :key="item.label"></tree-node>
</template>

<script setup>
import { toRefs } from "vue";
import TreeNode from "./TreeNode.vue";

const props = defineProps({
  data: Object, // Tree ma'lumotlarini olish uchun prop
})
const { data } = toRefs(props)
</script>