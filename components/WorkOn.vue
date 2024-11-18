<template>
    <section class="container mx-auto mt-5">
        <h2 class="text-2xl font-normal mb-4">Work On</h2>

        <div class="grid grid-cols-4 gap-2">
            <div v-for="project in projects" :key="i" class="border border-slate-500 rounded-md p-1 hover:bg-gradient-to-t hover:animate-wiggle animate-ease-in-out hover:from-slate-800 hover:to-sky-900">
                <div class="p-2">
                    <img :src="project.image" alt="" class="rounded-md">
                </div>
                <div class="px-2 pb-2">
                    <h1 class="text-xl font-normal mb-1">{{ project.name }}</h1>
                    <div class="grid grid-cols-8 gap-0">
                        <div  v-for="stack in project.stacks" :key="i">
                            <img v-if="stack.icon" class="w-5 h-5" :alt="stack.name" :src="stack.icon">
                        </div>
                    </div>
                    <h2 class="text-sm font-normal text-gray-400 pt-1">{{ project.description }}</h2>
                </div>
            </div>
            
        </div>
    </section>
</template>
<script>
export default {
    props: ['projects'],
    data() {
        return {
            
        }
    }
}
</script>
<style>
    
</style>