<template>
    <div class="skills">
        <label v-for="tech in technologies">
            <input type="checkbox">
            <div class="button" @click="filterCategory(tech)">{{ tech }}</div>
        </label>
    </div>
</template>

<script>
export default {
    name: "ProjectsFilter",
    data() {
        return {
            activeCategory: [],
            technologies: [
                "C++",
                "C",
                "CMake",
                "Python",
                "Javascript",
                "Vue.js",
                "Bootstrap",
                "HTML",
                "CSS",
                "OpenCV",
                "GTK",
                "Google Cloud",
                "AWS",
            ],
        }
    },
    methods: {
        filterCategory(category) {
            const index = this.activeCategory.indexOf(category);
            if (index < 0) {
                this.activeCategory.push(category);
            }
            else {
                this.activeCategory.splice(index, 1);
            }
            console.log(this.activeCategory)
            this.$emit("filter-projects", this.activeCategory);
        },
    },
}
</script>

<style scoped>
.skills {
    display: flex;
    /* justify-content: center; */
    flex-direction: row;
    flex-wrap: wrap;
    padding-bottom: 1em;
}

.button {
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    padding: 5px 10px;
    margin: 5px 5px 5px 0;
}

.button:hover {
    padding: 3px 8px;
    border: 3px solid var(--color-border);
}

input:checked+div {
    background: var(--color-border);
}

label > input {
    display: none;
}
</style>