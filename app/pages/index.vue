<template>
    <v-autocomplete v-model="selected" label="Select a state" :items="items" item-title="name" item-value="name"
        :loading="loading" clearable class="w-50" />

    <v-btn size="default" color="success" @click="save"><i class="fa fa-save fa-xl mr-2"></i>Small Button</v-btn>


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
}
</script>
