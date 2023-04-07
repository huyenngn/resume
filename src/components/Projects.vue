<template>
    <Filter @filter-projects="updateFilterList" />
    <div v-for="(project, index) in filteredProjects" :key="index">
        <Item v-bind:project="project" v-bind:class="{ card: index != projects.length - 1 }"></Item>
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
        updateFilterList(filter) {
            this.filterList = filter;
        },
    },
    computed: {
        filteredProjects() {
            return this.projects.filter((project) =>
                this.filterList.every(tech => project.technologies.includes(tech))
            );
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
                    text: "Auto-Typer for Linux",
                    github: "",
                    link: "",
                    technologies: ["C", "CMake", "GTK"],
                },
                {
                    title: "Twitter Bot",
                    text: "Automated Translation Twitter Bot",
                    github: "puta",
                    link: "",
                    technologies: ["Python", "Javascript", "Google Cloud", "Docker", "AWS"],
                },
                {
                    title: "Ribbon Designer",
                    text: "Web App for Designing Satin Ribbons for Printing",
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