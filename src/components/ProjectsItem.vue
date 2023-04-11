<template>
  <div>
            <h4>{{ project.title }}</h4>
        <div>{{ project.text }}</div>
           <div class="technologies">
        <div class="technology" v-for="tech in project.technologies">
            {{tech}}
        </div>
            </div>
        <div class="technologies" >
            <a :href="project.github"><div class="icon" v-if="project.github"><IconGithub /></div></a>
            <a :href="project.git"><img class="icon" v-if="project.git" src="/src/assets/git.png" /></a>
            <a :href="project.link"><img class="icon"  v-if="project.link" src="/src/assets/link.png" /></a>
        </div>
        
  </div>

</template>

<script>
import IconGithub from './icons/IconGithub.vue';

  export default {
    name: "ChirpContainer",
    props: {
        project: {
            type: Object,
            required: true
        }
    },
    components: { IconGithub }
};
</script>

<style scoped>
.technologies {
display: flex;
flex-wrap: wrap;
margin: 1em auto;
}

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
    margin-right: 1em;
    display: flex;
    place-items: center;
    place-content: center;
  }

  .technology {
    margin-right: 1rem;
    color: grey;
  }

  a {
text-decoration: none;
  color: var(--color-text);
  transition: 0.4s;
}
</style>