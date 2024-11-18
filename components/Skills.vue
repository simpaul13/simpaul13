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
               'animate-delay-500',
               isBackendVisible
                  ? 'animate-fade-down intersect-opacity-100'
                  : 'intersect-opacity-0'
            ] : 
            skill.name === 'Tools' ? [
               'animate-delay-1000',
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
   props: ["skills"],
   data() {

      return {
         loading: true,
         isFrontendVisible: true,
         isBackendVisible: true,
         isToolsVisible: true,
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
