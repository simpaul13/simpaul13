<template>
   <section class="container mx-auto mt-5">
     <h2 class="text-2xl font-normal mb-4">Skills</h2>
     <hr class="h-px my-3 bg-gray-200 border-0 dark:bg-gray-700" />
 
     <!-- Frontend Section -->
     <div
       ref="frontendSection"
       id="frontendSection"
       :class="[
         'animate-once animate-ease-in-out animate-delay-100',
         isFrontendVisible
           ? 'animate-fade-down intersect-opacity-100'
           : 'animate-fade-up intersect-opacity-0',
       ]"
     >
       <h3 class="text-lg mb-2">Frontend</h3>
       <ul class="grid grid-cols-1 md:grid-cols-4 gap-1">
         <li
           v-for="frontendSkill in frontendSkills"
           :key="frontendSkill.name"
           class="border border-slate-700 text-white p-2 rounded-md hover:bg-gradient-to-r hover:from-slate-800"
           :class="frontendSkill.tobgSkill"
         >
           <div class="flex items-center">
             <div
               class="rounded-md bg-opacity-20 w-9 h-9 mr-2 flex items-center justify-center"
               :class="frontendSkill.bgSkill"
             >
               <img
                 :src="frontendSkill.icon"
                 :alt="frontendSkill.name"
                 class="w-6 h-6"
               />
             </div>
             <span class="font-medium">{{ frontendSkill.name }}</span>
           </div>
         </li>
       </ul>
     </div>
 
     <!-- Backend Section -->
     <div
       ref="backendSection"
       :class="[
         'animate-once animate-ease-in-out animate-delay-300',
         isBackendVisible
           ? 'animate-fade-down intersect-opacity-100'
           : 'animate-fade-up intersect-opacity-0',
       ]"
     >
       <h3 class="text-lg mt-4 mb-2">Backend</h3>
       <ul class="grid grid-cols-1 md:grid-cols-4 gap-1">
         <li
           v-for="backendSkill in backendSkills"
           :key="backendSkill.name"
           class="border border-slate-700 text-white p-2 rounded-md hover:bg-gradient-to-r hover:from-slate-800"
           :class="backendSkill.tobgSkill"
         >
           <div class="flex items-center">
             <div
               class="rounded-md bg-opacity-20 w-9 h-9 mr-2 flex items-center justify-center"
               :class="backendSkill.bgSkill"
             >
               <img
                 :src="backendSkill.icon"
                 :alt="backendSkill.name"
                 class="w-6 h-6"
               />
             </div>
             <span class="font-medium">{{ backendSkill.name }}</span>
           </div>
         </li>
       </ul>
     </div>
 
     <!-- Tools Section -->
     <div
       ref="toolsSection"
       :class="[
         'animate-once animate-ease-in-out animate-delay-500',
         isToolsVisible
           ? 'animate-fade-down intersect-opacity-100'
           : 'animate-fade-up intersect-opacity-0',
       ]"
     >
       <h3 class="text-lg mt-4 mb-2">Tools</h3>
       <ul class="grid grid-cols-1 md:grid-cols-4 gap-1">
         <li
           v-for="toolSkill in toolsSkills"
           :key="toolSkill.name"
           class="border border-slate-700 text-white p-2 rounded-md hover:bg-gradient-to-r hover:from-slate-800"
           :class="toolSkill.tobgSkill"
         >
           <div class="flex items-center">
             <div
               class="rounded-md bg-opacity-20 w-9 h-9 mr-2 flex items-center justify-center"
               :class="toolSkill.bgSkill"
             >
               <img
                 :src="toolSkill.icon"
                 :alt="toolSkill.name"
                 class="w-6 h-6"
               />
             </div>
             <span class="font-medium">{{ toolSkill.name }}</span>
           </div>
         </li>
       </ul>
     </div>
   </section>

</template>
 
<script>
 import { ref, onMounted } from "vue";
 
 export default {
   data() {
     return {
      loading: true,
       isFrontendVisible: true,
       isBackendVisible: true,
       isToolsVisible: true,
         frontendSkills: [
            {
               name: "Vue",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg",
               bgSkill: "bg-green-500",
               tobgSkill: "hover:to-green-500",
            },
            {
               name: "Nuxt",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nuxtjs/nuxtjs-original.svg",
               bgSkill: "bg-green-500",
               tobgSkill: "hover:to-green-500",
            },
            {
               name: "Tailwind",
               icon: "https://raw.githubusercontent.com/devicons/devicon/6910f0503efdd315c8f9b858234310c06e04d9c0/icons/tailwindcss/tailwindcss-original.svg",
               bgSkill: "bg-sky-500",
               tobgSkill: "hover:to-sky-500",
            },
            {
               name: "HTML",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg",
               bgSkill: "bg-orange-500",
               tobgSkill: "hover:to-orange-500",
            },
            {
               name: "CSS",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg",
               bgSkill: "bg-blue-500",
               tobgSkill: "hover:to-blue-500",
            },
            {
               name: "JavaScript",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg",
               bgSkill: "bg-yellow-500",
               tobgSkill: "hover:to-yellow-500",
            },
         ],
         backendSkills: [
            {
               name: "PHP",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg",
               bgSkill: "bg-blue-900",
               tobgSkill: "hover:to-blue-900",
            },
            {
               name: "Laravel",
               icon: "https://raw.githubusercontent.com/devicons/devicon/6910f0503efdd315c8f9b858234310c06e04d9c0/icons/laravel/laravel-original.svg",
               bgSkill: "bg-red-500",
               tobgSkill: "hover:to-red-500",
            },
            {
               name: "MySQL",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg",
               bgSkill: "bg-blue-500",
               tobgSkill: "hover:to-blue-500",
            },
            {
               name: "AdonisJS",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/adonisjs/adonisjs-original.svg",
               bgSkill: "bg-blue-900",
               tobgSkill: "hover:to-blue-900",
            },
         ],
         toolsSkills: [
            {
               name: "Git",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg",
               bgSkill: "bg-orange-700",
               tobgSkill: "hover:to-orange-700",
            },
            {
               name: "NPM",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/npm/npm-original-wordmark.svg",
               bgSkill: "bg-red-500",
               tobgSkill: "hover:to-red-500",
            },
            {
               name: "GitHub",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg",
               bgSkill: "bg-gray-500",
               tobgSkill: "hover:to-gray-500",
            },
            {
               name: "Visual Studio Code",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg",
               bgSkill: "bg-blue-500",
               tobgSkill: "hover:to-blue-500",
            },
            {
               name: "Postman",
               icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postman/postman-original.svg",
               bgSkill: "bg-orange-700",
               tobgSkill: "hover:to-orange-700",
            },
            {
               name: "Ubuntu",
               icon: "https://raw.githubusercontent.com/devicons/devicon/6910f0503efdd315c8f9b858234310c06e04d9c0/icons/ubuntu/ubuntu-original.svg",
               bgSkill: "bg-orange-600",
               tobgSkill: "hover:to-orange-600",
            },
         ],
      };
  },
  mounted() {
      this.setupIntersectionObservers();
  },
  methods: {
    async setupIntersectionObservers() {
      const options = {
        threshold: 0.3,
      };

      const handleIntersection = (entries, observer, section) => {
        entries.forEach((entry) => {
          this[section] = entry.isIntersecting;
        });
      };

      const frontendObserver = new IntersectionObserver((entries) =>
        handleIntersection(entries, frontendObserver, "isFrontendVisible"),
        options
      );
      frontendObserver.observe(this.$refs.frontendSection);

      const backendObserver = new IntersectionObserver((entries) =>
        handleIntersection(entries, backendObserver, "isBackendVisible"),
        options
      );
      backendObserver.observe(this.$refs.backendSection);

      const toolsObserver = new IntersectionObserver((entries) =>
        handleIntersection(entries, toolsObserver, "isToolsVisible"),
        options
      );
      toolsObserver.observe(this.$refs.toolsSection);
    },
  },
};
</script>

<style scoped>
.intersect-opacity-0 {
  opacity: 0;
}
.intersect-opacity-100 {
  opacity: 1;
}
</style>