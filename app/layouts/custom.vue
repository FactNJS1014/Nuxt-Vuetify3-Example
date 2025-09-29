<script>
import Sidebar from '~/components/sidebar.vue';
</script>

<template>
    <v-layout class="rounded border">
        <v-app-bar title="Application bar"></v-app-bar>

        <Sidebar />

        <v-main class="d-flex align-center justify-center" style="height: 300px;">
            <v-container>
                <slot />
            </v-container>
        </v-main>


    </v-layout>
</template>