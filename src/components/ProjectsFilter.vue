<template>
    <div class="skills">
        <div class="button" v-for="tech in technologies">{{tech}}</div>
    </div>
</template>

<script>
export default {
    name: "ProjectsFilter",
    data() {
        return {
            active: '',
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
    // methods: {
    //     // TODO
    //     filterCategory(category) {
    //         this.activeCategory = category
    //         this.$emit("filter-chirps", this.activeCategory);
    //     },
    //     filterHashtag() {
    //         this.$emit("filter-chirps", this.hashtag)
    //         this.$refs.hashinput.value = '';
    //     },
    //     addChirp(chirp) {
    //         this.newChirp = chirp
    //         this.$emit("added-chirp", this.newChirp);
    //     }
    // },
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
    /* display: inline-flex; */
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    padding: 5px 10px;
    margin: 5px 5px 5px 0;
}

.button:hover {
    background: var(--color-border);
}
</style>