<template>
    <v-autocomplete v-model="selected" :items="items" item-title="name" item-value="name" label="Select a state"
        clearable class="w-50">
        <!-- icon ด้านซ้าย -->
        <template #prepend-inner>
            <i class="fa fa-search mr-2"></i>
        </template>

        <!-- แสดงข้อความเมื่อไม่มีข้อมูล -->
        <template #no-data>
            <div class="text-red-500 ms-3">No states found</div>
        </template>
    </v-autocomplete>

    <v-radio-group inline v-model="radios">
        <v-radio label="Radio One" value="one"></v-radio>
        <v-radio label="Radio Two" value="two"></v-radio>
        <v-radio label="Radio Three" value="three"></v-radio>
    </v-radio-group>

    <v-checkbox label="Checkbox"></v-checkbox>


    <v-btn size="default" color="success" @click="save" class="rounded">
        <template #prepend>
            <i class="fa fa-save fa-md mr-1"></i>
        </template>
        Save
        <template #append>
            <i class="fa fa-check fa-sm ml-1"></i>
        </template>
    </v-btn>


</template>

<script setup>
import { ref, onMounted } from "vue"
import axios from "axios"


definePageMeta({
    layout: 'custom'
})

const items = ref([])
const selected = ref(null)
const loading = ref(false)
const radios = ref('one')

onMounted(async () => {
    loading.value = true
    try {
        // ตัวอย่าง API → เปลี่ยน URL ตามจริง
        const res = await axios.get('https://nuxt-api-alpha.vercel.app/api/material/list')
        // สมมติ API ส่งกลับ [{id: 1, name: 'California'}, {id: 2, name: 'Texas'}]
        items.value = res.data.results
    } catch (err) {
        console.error("Error fetching data:", err)
    } finally {
        loading.value = false
    }
})

const save = () => {
    console.log("Selected is " + selected.value)
    console.log("Radio is " + radios.value)
}
</script>
