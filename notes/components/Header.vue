<script lang="ts" setup>
import { useAuthStore } from "~/stores/auth"
const authStore = useAuthStore();
const isAuthenticated = ref();
const router = useRouter();

isAuthenticated.value = useCookie("access_token").value;

const logout = async () => {
    await authStore.logout();
    const accessToken = useCookie("access_token");
    const refreshToken = useCookie("refresh_token");
    accessToken.value = null;
    refreshToken.value = null;
    setTimeout(() => {
        isAuthenticated.value = useCookie("access_token").value;
    }, 100);
    router.push({
        path: "/"
    })
}
</script>
<template>
    <header class="w-full border-b border-slate-200 py-6 shadow-[0_30px_60px_rgba(0,0,0,0.09)]">
        <div class="container">
            <div class="flex justify-between items-center">
                <div>
                    <NuxtLink to="/" class="text-xl font-bold">NoteG</NuxtLink>
                </div>
                <nav class="flex items-center gap-6">

                    <NuxtLink to="/product" class="text-base">Note</NuxtLink>
                    
                    <NuxtLink to="/product/create" class="text-base">New</NuxtLink>

                    <NuxtLink v-if="!isAuthenticated" to="/login" class="text-base bg-blue-600
px-6 py-2 text-white rounded-lg hover:bg-blue-600/80">Login</NuxtLink>
<div v-else class="text-base cursor-pointer bg-red-600 px-6 py-2 text-white
rounded-lg hover:bg-red-600/80" @click="logout">Logout</div>

                </nav>
            </div>
        </div>
    </header>
</template>