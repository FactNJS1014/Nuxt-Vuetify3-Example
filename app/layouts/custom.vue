<script setup>
import Sidebar from '~/components/sidebar.vue'
</script>

<template>
    <v-app>
        <!-- App Bar -->
        <v-app-bar app color="blue">
            <v-app-bar-title>Application bar</v-app-bar-title>
        </v-app-bar>

        <!-- Sidebar + Main -->
        <Sidebar />

        <v-main class="p-4">
            <v-container>
                <slot />
            </v-container>
        </v-main>
    </v-app>
</template>
