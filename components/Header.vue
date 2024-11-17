<template>
  <nav :class="navClasses">
    <!-- Gradient Overlay -->
    <div
      v-if="!isScrolled"
      class="absolute inset-0 h-16 bg-gradient-to-b from-gray-800 to-transparent pointer-events-none"
    ></div>

    <div class="container mx-auto px-4 py-4 relative z-10">
      <div class="flex items-center justify-between">
        <!-- Brand Logo -->
        <div :class="['font-bold', textClasses, brandTextSize]" v-if="navSettings.showBrand === true">
          Brand
        </div>

        <!-- Hamburger Menu (Mobile) -->
        <div class="md:hidden">
          <button
            @click="toggleMenu"
            :class="[textClasses, 'focus:outline-none']"
            aria-label="Toggle navigation menu"
          >
            <svg
              class="w-6 h-6"
              fill="none"
              :stroke="iconStrokeColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              ></path>
            </svg>
          </button>
        </div>

        <!-- Navigation Links (Desktop) -->
        <div class="hidden md:flex flex-1 space-x-8" 
            :class="navSettings.navLinkPosition === 'justify-center' ?  'justify-center' : 
            navSettings.navLinkPosition === 'justify-end' ? 'justify-end' : 'justify-start'">
            <div v-for="link in navLinks" :key="link.name">
                <a
                    v-if="link.type === 'a'"
                    :href="link.href"
                    :class="[textClasses, linkHoverClasses, navLinkTextSize]"
                >
                {{ link.name }}
                </a>
                <router-link
                    v-if="link.type === 'router-link'"
                    :to="link.href"
                    :class="[textClasses, linkHoverClasses, navLinkTextSize]"
                >
                {{ link.name }}
                </router-link>
            </div>

            <!-- Switch to Light/Dark Mode -->
            <button
                @click="toggleColorMode"
                class="focus:outline-none"
              >
                <svg
                  class="w-6 h-6"
                  :class="[textClasses]"
                  fill="none"
                  :stroke="iconStrokeColor"
                  viewBox="0 0 24 24"
                  v-if="colorMode === 'light'"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"
                  ></path>
                </svg>
                <svg
                  class="w-6 h-6"
                  :class="[textClasses]"
                  fill="none"
                  :stroke="iconStrokeColor"
                  viewBox="0 0 24 24"
                  v-else
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"
                  ></path>
                </svg>
            </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu -->
    <transition name="fade">
      <div
        v-if="isMenuOpen"
        class="md:hidden fixed inset-0 dark:bg-gray-800 dark:bg-opacity-95 dark:text-white  bg-opacity-95 z-40"
      >
        <div class="container text-center mx-auto px-4 py-4" v-for="link in navLinks" :key="link.name">
            <a
                v-if="link.type === 'a'"
                :href="link.href"
                class="block px-4 py-2 rounded"
                @click="toggleMenu"
                :class="mobileNavLinkTextSize"
            >
                {{ link.name }}
            </a>
            <router-link
                v-if="link.type === 'router-link'"
                :to="link.href"
                class="block px-4 py-2 rounded"
                @click="toggleMenu"
                :class="mobileNavLinkTextSize"
            >
                {{ link.name }}
            </router-link>
        </div>
      </div>
    </transition>
  </nav>
</template>
<script>
  import data from '~/assets/js/data.json';

  export default {
    
    data() {
      return {
        navSettings: data.navSettings,
        navLinks: data.navLinks,
        isMenuOpen: false,
        isScrolled: false,
        colorMode: null,
      };
    },
    computed: {
      navClasses() {
        const baseClasses =
          'fixed w-full z-50 transition-all duration-300 ease-in-out';
        const scrolledBackground = 'dark:bg-slate-800 bg-stone-200 shadow-md';
        return [
          baseClasses,
          this.isScrolled ? scrolledBackground : 'bg-transparent',
        ];
      },
      textClasses() {
        return this.isScrolled ? 'dark:text-white text-gray-800' : 'text-white';
      },
      linkHoverClasses() {
        return 'hover:text-blue-300 transition duration-200';
      },
      iconStrokeColor() {
        return this.isScrolled ? 'currentColor' : '#ffffff';
      },
      brandTextSize() {
        return 'text-2xl md:text-xl';
      },
      navLinkTextSize() {
        return 'text-lg';
      },
      mobileNavLinkTextSize() {
        return 'text-xl';
      },
    },
    mounted() {
      // Initialize color mode from saved preference or system preference
      const savedColorMode = localStorage.getItem('color-mode');
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;

      this.colorMode = savedColorMode || (prefersDark ? 'dark' : 'light');
      this.$colorMode.preference = this.colorMode; // Set the app's color mode
      document.documentElement.classList.toggle('dark', this.colorMode === 'dark');

      // Add scroll event listener
      window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
      toggleMenu() {
        this.isMenuOpen = !this.isMenuOpen;
      },
      closeMenu() {
        this.isMenuOpen = false;
      },
      handleScroll() {
        this.isScrolled = window.scrollY > 0;
      },
      toggleColorMode() {
        this.colorMode = this.colorMode === 'light' ? 'dark' : 'light';
        this.$colorMode.preference = this.colorMode;

        // Save color mode preference to local storage
        localStorage.setItem('color-mode', this.colorMode);

        // Toggle dark mode class on the root element
        document.documentElement.classList.toggle('dark', this.colorMode === 'dark');
      },
    },
  };
</script>

<style scoped>
  /* Gradient Overlay Fix */
  nav .gradient-overlay {
    height: 4rem;
  }

  /* Mobile Menu Transition */
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.3s ease;
  }
  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
</style>