<template>
  <table v-if="column.length || data.length">
    <thead>
      <tr>
        <th v-for="col in column" :key="col.key" class="py-3 text-left">
          {{ col.label }}
        </th>
      </tr>
    </thead>
    <tbody class="table-row-group">
      <tr v-for="item in data" :key="item.id" class="border-t border-t-gray-300">
        <td v-for="key in displayedFieldKeys" :key="key" class="pr-[20px] py-2">
          <slot
            :name="`cell(${key})`"
            :value="item[key]"
            :item="item"
          >
            {{ item[key] }}
          </slot>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { toRefs, computed } from "vue";

const props = defineProps({
  column: Array,
  data: Array
})

const { column, data } = toRefs(props)

const displayedFieldKeys = computed(() => {
  return Object.entries(column.value).map(([_key, value]) => value.key)
})
</script>