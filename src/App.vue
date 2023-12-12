<template>
  <div class="flex flex-col gap-6 p-6 pb-0">
    <!-- For Collapse -->
    <div>
      <TreeComp :data="treeData" />
    </div>
    <!-- For Table -->
    <div>
      <TableComp :column="tableColumns" :data="tableRow">
        <template #cell(name)="{ value }">
          <a href="#" class="text-blue-600">{{ value }}</a>
        </template>
        <template #cell(tags)="{ value }">
          <div>
            <span v-for="(tag,index) in value" :key="tag" 
              class="rounded-md tagsGood px-2 pb-1"
              :class="{'tagsBad': tag === 'loser', 'tagsBad': tag === 'loser', 'tagsJob': index === 1}"
            >
              {{ tag }}
            </span>
          </div>
        </template>

        <template #cell(action)="{ value, item }">
          <div class="flex gap-2">
            <a href="#" class="text-blue-600">Invite - {{ item.name }}</a>
            <button class="text-blue-600">delete</button>
            <p class="text-blue-600">more action</p>
          </div>
        </template>
      </TableComp>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TreeComp from "./components/TreeCollapse/TreeComp.vue";
import TableComp from "./components/Table/TableComp.vue";

/* === Data of Tree Collapse === */
const treeData = ref([
  {
    label: 'Element 1',
    children: [
      {
        label: 'Element 1.1',
        children: [
          {
            label: 'Element 1.1.1'
          },
        ]
      },
      {
        label: 'Element 1.2',
        children: [
          {
            label: 'Element 1.2.1',
            children: [
              {
                label: 'Element 1.2.1.1',
                children: [
                  {
                    label: 'Element 1.2.1.1.1'
                  }
                ]
              },
              {
                label: 'Element 1.2.1.2'
              }
            ]
          },
          {
            label: 'Element 1.2.2'
          }
        ]
      },
      {
        label: 'Element 1.3',
        children: [
          {
            label: 'Element 1.3.1'
          },
        ]
      }
    ],
  },
  {
    label: 'Element 2',
    children: [
      {
        label: 'Element 1.2.1',
        children: [
          {
            label: 'Element 1.2.1.1',
            children: [
              {
                label: 'Element 1.2.1.1.1',
              }
            ]
          }
        ]
      },
      {
        label: 'Element 1.2.2',
        children: [
          {
            label: 'Element 1.2.2.1'
          },
          {
            label: 'Element 1.2.2.2'
          }
        ]
      }
    ]
  },
  {
    label: 'Element 3',
    children: [
      {
        label: 'Element 3.1'
      },
      {
        label: 'Element 3.2',
        children: [
          {
            label: 'Element 3.2.1'
          },
          {
            label: 'Element 3.2.2'
          }
        ]
      },
      {
        label: 'Element 3.3',
        children: [
          {
            label: 'Element 3.3.1'
          },
          {
            label: 'Element 3.3.2'
          }
        ]
      },
      {
        label: 'Element 3.4'
      }
    ]
  }
]);

/* === Data of For Tabkle === */

// Table Column data
const tableColumns = ref([
  { key: 'name', label: '🙂 Name' },
  { key: 'age', label: 'Age' },
  { key: 'address', label: 'Address' },
  { key: 'tags', label: 'Tags' },
  { key: 'action', label: 'Action' },
])

// Table Row data
const tableRow = ref([
  { id: 1, name: 'John Brown', age: 32, address:"New York No. 1 Lake Park", tags:['nice','developer'], action: 'invite'},
  { id: 1, name: 'Jim Green', age: 42, address:"London No. 1 Lake Park", tags:['loser'], action: 'invite'},
  { id: 1, name: 'Joe Black', age: 32, address:"Sidney No. 1 Lake Park", tags:['cool','teahcer'], action: 'invite'}
])
</script>
<style lang="css">
.tagsGood {
  @apply bg-[#F6FFEC] border border-[#D3F2BA] text-[#6BB64B]
}
.tagsBad {
  @apply bg-[#FFF2E8] border border-[#FFC2A1] text-[#D84C25]
}
.tagsJob {
  @apply bg-[#F0F5FF] border border-[#BDD0FD] text-[#2741C5]
}
</style>