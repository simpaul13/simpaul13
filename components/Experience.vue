<template>
    <section class="container mx-auto mt-5" id="experience">
        <h2 class="text-2xl font-normal mb-4">Experience</h2>

        <ul class="grid grid-cols-1 md:grid-cols-1 gap-2">
            <li 
                class="" 
                :class="
                career.title === 'Junior Web Developer' ? [
                    isCareerVisible0  ?
                    'animate-fade-right animate-once animate-ease-in-out animate-delay-500' :
                    'intersect-opacity-0'
                ] : 
                career.title === 'Computer Technician (MIS)' ? [
                    isCareerVisible1  ?
                    'animate-fade-left animate-once animate-ease-in-out animate-delay-500' :
                    'intersect-opacity-0'
                ] : ''
                "
                v-for="career, index in careers" 
                :key="career.title" 
                :ref="(el) => (refs['careerSection' + index] = el)"
            >
                <div class="grid grid-cols-2 container px-56 mb-2 border border-slate-500 rounded-md p-2 ">
                    <div class="flex flex-col">
                        <h1 class="text-base font-light w-full">{{ career.yearStart }} - {{ career.yearEnd }}</h1>
                    </div>
                    <div class="flex flex-col justify-center">
                        <h1 class="text-xl font-normal w-full mb-1">{{ career.company }}</h1>
                        <h2 class="text-sm font-normal w-full text-gray-400">{{ career.title }}</h2>
                    </div>
                </div>
            </li>
        </ul>
    </section>
</template>
<script>
export default {
    data() {
        return {
            isCareerVisible0: true,
            isCareerVisible1: true,
            careers : [
                {
                    yearStart: 'March, 2021',
                    yearEnd: 'Present',
                    title: 'Junior Web Developer',
                    company: 'HMR Philippines Inc.',
                    animation: 'animate-fade-right animate-once animate-ease-in-out animate-delay-500',
                },
                {
                    yearStart: 'January, 2019',
                    yearEnd: 'March, 2020',
                    title: 'Computer Technician (MIS)',
                    company: 'ICCT Collages Inc.',
                    animation: 'animate-fade-left animate-once animate-ease-in-out animate-delay-500',
                }
            ],
            refs: {},
        }
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

            for (let index = 0; index < this.careers.length; index++) {
                console.log(`isCareerVisible${index}`);
                observeSection("careerSection" + index, `isCareerVisible${index}`);
            }
        }
    },
    mounted() {
        this.setupIntersectionObservers();
    }
}
</script>
<style scoped>
    
</style>