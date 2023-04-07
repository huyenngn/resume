<template>
    <div>
        <h4>{{ project.title }}</h4>
        <div>{{ project.text }}</div>
        <div class="technology" v-for="tech in project.technologies">
            {{tech}}
        </div>
        <div >
            <a :href="project.github"></a><img class="icon" v-if="project.github" src="src/assets/github.png" />
            <a :href="project.link"></a><img class="icon"  v-if="project.link" src="src/assets/link.png" />
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