<template>
    <div class="sc-page sc-flex-center">
        <BackButton name="Projects" class="absolute left-5 top-5" />

        <div class="content sc-flex-center w-9/10 mt-25 mb-5">
            <div class="grid w-full grid-cols-1 gap-10 md:w-auto md:grid-cols-2">
                <Suspense>
                    <ProjectList />

                    <template #fallback>
                        <ProjectListSkeleton />
                    </template>
                </Suspense>

                <!-- <ProjectListSkeleton /> -->
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
    useHead({
        title: 'Projects'
    })
</script>
