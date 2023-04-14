<template>
    <div class="skills">
        <label v-for="tech in technologies">
            <input type="checkbox">
            <div class="button" @click="filterCategory(tech)">{{ tech }}</div>
        </label>
        <label>
            <input type="button">
            <div class="button" @click="resetFilter()"> &#10060; </div>
        </label>
    </div>
</template>

<script>
export default {
    name: "ProjectsFilter",
    data() {
        return {
            activeCategory: [],
        }
    },
    props: {
        technologies: {
            type: Array,
            required: true
        },
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
        resetFilter() {
            this.activeCategory = []
            document.querySelectorAll('input[type=checkbox]').forEach(el => el.checked = false);
            console.log(this.activeCategory)
            this.$emit("filter-projects", this.activeCategory);
        },
    },
}
</script>

<style scoped>
.skills {
    min-width: 0;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    padding-bottom: 1em;
}

label>input {
    display: none;
}
</style>