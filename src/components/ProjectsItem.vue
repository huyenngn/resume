<template>
    <div>
        <h4>{{ project.title }}</h4>
        <div>{{ project.text }}</div>
        <div class="technology" v-for="tech in project.technologies">
            {{tech}}
        </div>
        <div >
            <a :href="project.github"><img class="icon" v-if="project.github" src="/src/assets/github.png" /></a>
            <a :href="project.git"><img class="icon" v-if="project.git" src="/src/assets/git.png" /></a>
            <a :href="project.link"><img class="icon"  v-if="project.link" src="/src/assets/link.png" /></a>
        </div>
    </div>
</template>

<script>
export default {
    name: "ChirpContainer",
    props: {
      project: {
        type: Object,
        required: true
      }
    }
  };
</script>

<style scoped>
  h4 {
    font-size: 1em;
    font-weight: 500;
    margin-bottom: 0.4rem;
    color: var(--color-heading);
  }

  a:hover {
    background-color: var(--color-background);
  }

  .icon {
    width: 1rem;
    height: 1rem;
    margin: 1em 1em 0 0;
  }

  .technology {
    display: inline;
    margin-right: 1rem;
    color: grey;
  }
</style>