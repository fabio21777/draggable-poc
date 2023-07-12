<template>
    <el-table :data="list" style="width: 100%">
        <el-table-column prop="id" label="ID" width="180"></el-table-column>
        <el-table-column prop="name" label="Name" width="180"></el-table-column>
        <draggable class="dragArea list-group w-full" :list="list" @change="log">
            <div class="list-group-item bg-gray-300 m-1 p-3 rounded-md text-center" v-for="element in list"
                :key="element.name">
                {{ element.name }}
            </div>
        </draggable>
    </el-table>
</template>
  
<script lang="ts">
import { defineComponent, ref } from 'vue'
import { ElTable, ElTableColumn } from 'element-plus'
import { VueDraggableNext } from 'vue-draggable-next'



    interface ListItem {
    name: string
    id: number
}

export default defineComponent({
    name: 'DroggableTable',
    components: {
        ElTable,
        ElTableColumn,
        draggable: VueDraggableNext,
    },
    setup() {
        const list = ref<ListItem[]>([
            { name: 'John', id: 1 },
            { name: 'Joao', id: 2 },
            { name: 'Jean', id: 3 },
            { name: 'Gerard', id: 4 },
        ])

        const log = (event: Event) => {
            console.log(event)
        }

        return {
            list,
            log,
        }
    },
})
</script>
  