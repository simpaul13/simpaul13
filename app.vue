<template>
  <div class="dark:bg-slate-800 bg-stone-200 dark:text-gray-300">
    <Header :navSettings="navSettings" :navLinks="navLinks" />
    <NuxtRouteAnnouncer />
    <NuxtWelcome />
    <Experience />
    <WorkOn :projects="projects" />
    <Skills :skills="skills" />
    <Footer />
  </div>
</template>
<script>
import data from "~/assets/js/data.json";
export default {
  data() {
    return {
      navSettings: data.navSettings,
      navLinks: data.navLinks,
      socialLinks: data.socialLinks,
      skills: data.skills,
      projects: data.projects,
    };
  }
}
</script>