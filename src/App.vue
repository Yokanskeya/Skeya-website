<template>
    <RouterView v-slot="{ Component, route }">
        <Transition
            :enter-active-class="route.meta.enter as string"
            :leave-active-class="route.meta.leave as string"
            :after-enter="() => (show_ = true)"
        >
            <KeepAlive>
                <component :is="Component" :key="route.path" />
            </KeepAlive>
        </Transition>
    </RouterView>
</template>

<script setup lang="ts">
    import { useThemeStore } from './stores/theme'

    const themeStore = useThemeStore()
    const theme = computed(() => themeStore.theme)

    const show_ = ref(false)

    useHead({
        titleTemplate: (title?: string) => (title ? `${title} | Skeya` : 'Skeya'),
        link: [{ rel: 'icon', type: 'image/png', sizes: 'any', href: '/favicon.png' }]
    })

    // watch effect
    watchEffect(() => {
        if (theme.value) {
            document.documentElement.classList.remove('dark')
            document.documentElement.classList.add('light')
        } else {
            document.documentElement.classList.remove('light')
            document.documentElement.classList.add('dark')
        }
    })

    onMounted(() => {
        show_.value = true
    })
</script>

<style></style>
