<template>
    <section class="container mx-auto">

       
            <ul class="grid grid-cols-1 md:grid-cols-4 gap-1">
                <li v-for="skill in skills" :key="skill.name" class="bg-slate-900 text-white p-2 rounded-md">
                    <div class="flex items-center">
                        
                        <div class="rounded-md bg-opacity-20 w-9 h-9 mr-2 flex items-center justify-center" :class="skill.bgSkill">
                            <img :src="skill.icon" :alt="skill.name" class="w-6 h-6">
                        </div>
                        <span>{{ skill.name }}</span>
                    </div>
                </li>
            </ul>
    </section>
</template>
<script>

export default {
    data() {
        return {
            skills: [
                { name: 'HTML', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg', bgSkill: 'bg-orange-500' },
                { name: 'CSS', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg', bgSkill: 'bg-blue-500' },
                { name: 'JavaScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg', bgSkill: 'bg-yellow-500' },
                { name: 'Vue', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg', bgSkill: 'bg-green-500' },
                { name: 'Nuxt', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nuxtjs/nuxtjs-original.svg',  bgSkill: 'bg-green-500' },
                { name: 'Tailwind', icon: 'https://raw.githubusercontent.com/devicons/devicon/6910f0503efdd315c8f9b858234310c06e04d9c0/icons/tailwindcss/tailwindcss-original.svg', bgSkill: 'bg-sky-500' },
                { name: 'PHP', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg', bgSkill: 'bg-sky-500' },
                { name: 'Laravel', icon: 'https://raw.githubusercontent.com/devicons/devicon/6910f0503efdd315c8f9b858234310c06e04d9c0/icons/laravel/laravel-original.svg', bgSkill: 'bg-red-500' },
                { name: 'MySQL', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg', bgSkill: 'bg-sky-500' },
                { name: 'Git', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', bgSkill: 'bg-red-500' },
            ]
        }
    }
}
</script>
<style scoped>

</style>