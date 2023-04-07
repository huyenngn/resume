<template>
    <Filter />
    <div v-for="(project, index) in projects" :key="index">
        <Item v-bind:project="project" v-bind:class="{ card: index!=projects.length-1 }"></Item>
    </div>
</template>

<script>
import Filter from './ProjectsFilter.vue'
import Item from './ProjectsItem.vue'

export default {
    name: "App",
    components: {
        Filter,
        Item,
    },
    methods: {
        updateFilterString(filter) {
            this.filterString = filter;
        },
    },
    computed: {
        filteredProjects() {
            if (this.filterString.startsWith("#")) {
                return this.chirps.filter((chirp) =>
                    chirp.hashtags.includes(this.filterString)
                );
            } else {
                return this.chirps.filter(
                    (chirp) =>
                        !this.filterString || chirp.category.includes(this.filterString)
                );
            }
        },
    },
    data() {
        return {
            filterList: [],
            projects: [
                {
                    title: "Autonomous LEGO Car",
                    text: "Bachelor Project Software Engineering of Embedded Systems",
                    github: "ghj",
                    link: "meow",
                    technologies: ["C++", "CMake", "OpenCV"],
                },
                {
                    title: "LinuxTyper",
                    text: "Ich habe Lust auf ein Sandwich...",
                    github: "",
                    link: "",
                    technologies: ["C", "CMake", "GTK"],
                },
                {
                    title: "Twitter Bot",
                    text: "Ich habe Lust auf ein Sandwich...",
                    github: "puta",
                    link: "",
                    technologies: ["Python", "Javascript", "Google Cloud", "Docker", "AWS"],
                },
                {
                    title: "Ribbon Designer Web App",
                    text: "Ich habe Lust auf ein Sandwich...",
                    github: "",
                    link: "",
                    technologies: ["Javascript", "Vue.js", "Bootstrap", "HTML", "CSS"],
                },
            ],
        };
    },
};
</script>

<style>
.card {
    padding-bottom: 5px;
    margin-bottom: 5px;
    border-bottom: 1px solid var(--color-border);
    background: var(--color-background);
}
</style>