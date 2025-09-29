<template>
    <v-navigation-drawer app permanent class="bg-white">
        <v-list density="comfortable" nav>
            <v-list-item v-for="m in menu" :key="m.id" :title="m.label" :to="m.to" router exact
                :active="activemenu === m.name" @click="toggleMenu(m.name)">
                <!-- prepend slot สำหรับใส่ Font Awesome -->
                <template #prepend>
                    <i :class="[m.icon, 'fa-lg']" class="mr-2"></i>
                </template>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</template>

<script setup>
import { ref } from "vue";

const activemenu = ref("index");

const toggleMenu = (menu) => {
    activemenu.value = menu;
};

const menu = ref([
    {
        id: 1,
        name: "index",
        icon: "fa fa-home", // 👈 FA4 ใช้ fa fa-xxx (ไม่ใช่ fa-solid)
        to: "/",
        label: "Index",
    },
    {
        id: 2,
        name: "settings",
        icon: "fa fa-cog",
        to: "/settings",
        label: "Settings",
    },
    {
        id: 3,
        name: "contact",
        icon: "fa fa-file-text",
        to: "/contact",
        label: "Document",
    },
]);
</script>
