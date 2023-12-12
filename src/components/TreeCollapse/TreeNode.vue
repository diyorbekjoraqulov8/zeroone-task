<template>
  <li>
    <div 
      @click="toggleCollapse" 
      class="relative hover:bg-[#E0E0E0] flex items-center gap-2 cursor-pointer pl-2 pr-4 py-1 list__before"
    >
      <DropDownIcon 
        v-if="data.children" 
        class="w-[12px] h-[12px] transition-all" 
        :class="{'!-rotate-90':!isCollapsed}"
      />
      <p class=" w-full">{{ data.label }}</p>
    </div>
    <TransitionGroup name="list">
      <div v-if="data.children && isCollapsed" class="ml-[14px]">
        <tree-collapse :data="data.children"></tree-collapse>
      </div>
    </TransitionGroup>
  </li>
</template>

<script setup>
import { toRefs, ref } from "vue";
import TreeCollapse from "./TreeCollapse.vue";
import DropDownIcon from "../icons/DropDownIcon.vue";
const isCollapsed = ref(false);

const props = defineProps({
  data: Object, // Tree ma'lumotlarini olish uchun prop
})
const { data } = toRefs(props)

const toggleCollapse = () => {
  isCollapsed.value = !isCollapsed.value;
};
</script>

<style lang="css">
.list__before {
  @apply hover:before:w-[4px] before:h-full before:bg-blue-600 before:absolute before:left-0
}
</style>