<template>
    <Filter @filter-projects="updateFilterList" :technologies="getTechnologies()" />
    <div v-for="(project, index) in filteredProjects" :key="index">
        <Item v-bind:project="project" v-bind:class="{ card: index != projects.length - 1, lastcard: index == projects.length - 1 }"></Item>
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
        getTechnologies() {
            let technologies = [];
            this.projects.forEach(project => {
                project.technologies.forEach(tech => {
                    if (!technologies.includes(tech)) {
                        technologies.push(tech)
                    }
                });
            });
            return technologies;
        },
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
                    title: "🚗 Autonomous LEGO Car",
                    text: "Bachelor Project Software Engineering of Embedded Systems",
                    github: "",
                    git: "https://git.tu-berlin.de/sees-driving-1/raspberrypi",
                    link: "https://www.tu.berlin/sese/studium-lehre/studierendenprojeke\#c719986",
                    technologies: ["C++", "CMake", "OpenCV"],
                },
                {
                    title: "💻 LinuxTyper",
                    text: "Auto-Typer for Linux",
                    github: "https://github.com/huyenngn/linuxtyper",
                    git: "",
                    link: "",
                    technologies: ["C", "CMake", "GTK"],
                },
                {
                    title: "🤖 Twitter Bot",
                    text: "Automated Translation Twitter Bot",
                    github: "https://github.com/huyenngn/TwitterBot",
                    git: "",
                    link: "",
                    technologies: ["Python", "Javascript", "Google Cloud", "Docker", "AWS"],
                },
                {
                    title: "🎀 Ribbon Designer",
                    text: "Web App for Designing Satin Ribbons for Printing",
                    github: "https://github.com/huyenngn/RibbonDesigner",
                    git: "",
                    link: "https://tranquil-taffy-c57164.netlify.app/",
                    technologies: ["Javascript", "Vue.js", "Bootstrap", "HTML", "CSS"],
                },
                {
                    title: "🌐 Dynamic Portfolio Website",
                    text: "This Website",
                    github: "https://github.com/huyenngn/resume",
                    git: "",
                    link: "https://resume-huyenngn.vercel.app/",
                    technologies: ["Javascript", "Vue.js", "HTML", "CSS"],
                },
            ],
        };
    },
};
</script>

<style>
.card {
    min-width: 0;
    padding-bottom: 5px;
    margin-bottom: 5px;
    border-bottom: 1px solid var(--color-border);
    background: var(--color-background);
}

.lastcard {
  min-width: 0;
}
</style>