<template>
   <section class="container mx-auto mt-5">
      <h2 class="text-2xl font-normal mb-4">Skills</h2>
      <hr class="h-px my-3 bg-gray-200 border-0 dark:bg-gray-700" />

      <div 
         v-for="skill in skills" 
         :key="skill.name"
         :ref="(el) => (refs[skill.name.toLowerCase() + 'Section'] = el)"
         :class="[
            'animate-once animate-ease-in-out',
            skill.name === 'Frontend' ? [
               'animate-delay-100',
               isFrontendVisible
                  ? 'animate-fade-down intersect-opacity-100'
                  : 'intersect-opacity-0'
            ] :
            skill.name === 'Backend' ? [
               'animate-delay-300',
               isBackendVisible
                  ? 'animate-fade-down intersect-opacity-100'
                  : 'intersect-opacity-0'
            ] : 
            skill.name === 'Tools' ? [
               'animate-delay-500',
               isToolsVisible
                  ? 'animate-fade-down intersect-opacity-100'
                  : 'intersect-opacity-0'
            ] : '',
         ]"
         >
         <h3 
            class="text-lg font-semibold mb-2 mt-3">
            {{ skill.name }}
         </h3>

         <ul 
            class="grid grid-cols-1 md:grid-cols-4 gap-1">
            <li
               v-for="subSkill in skill.subSkills"
               :key="subSkill.name"
               class="border border-slate-500 dark:text-white p-2 rounded-md hover:bg-gradient-to-r"
               :class="[subSkill.tobgSkill, colorMode.value === 'dark' ? 'hover:from-slate-800' : 'hover:from-stone-200']">

               <div class="flex items-center">
                  <div
                     class="rounded-md bg-opacity-20 w-9 h-9 mr-2 flex items-center justify-center"
                     :class="subSkill.bgSkill"
                  >
                     <img
                        :src="subSkill.icon"
                        :alt="subSkill.name"
                        class="w-6 h-6"
                     />
                  </div>
                  <span class="text-sm">{{ subSkill.name }}</span>
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
         skills: [
            {
               name: "Frontend",
               subSkills: [
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
                  {
                     name: "Axios",
                     icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/axios/axios-plain.svg",
                     bgSkill: "bg-blue-800",
                     tobgSkill: "hover:to-blue-800",
                  }
               ],
            },
            {
               name: "Backend",
               subSkills: [
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
            },
            {
               name: "Tools",
               subSkills: [
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
            },
         ],
         refs: {},
      };
   },
   setup() {
      const colorMode = useColorMode();
      return { colorMode };
   },
   methods: {
    async setupIntersectionObservers() {
      // Wait for refs to be populated
      await nextTick();

      const options = { threshold: 0.3 };

      const observeSection = (refName, visibleState) => {
        const element = this.refs[refName];
        if (!element) {
          console.error(`Ref '${refName}' is not found or not an Element`);
          return;
        }

        const observer = new IntersectionObserver((entries) => {
          entries.forEach((entry) => {
            this[visibleState] = entry.isIntersecting;
          });
        }, options);

        observer.observe(element);
      };

      observeSection("frontendSection", "isFrontendVisible");
      observeSection("backendSection", "isBackendVisible");
      observeSection("toolsSection", "isToolsVisible");
    },
  },
  mounted() {
    this.setupIntersectionObservers();
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
