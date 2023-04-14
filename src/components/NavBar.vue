<template>
  <nav role='navigation'>
    <div class="button" @click="toggleTheme()">
      <span v-if="this.theme == 'darkMode'">&#9728;&#65039;</span>
      <span v-else>&#127769;</span>
    </div>
    <ul>
      <li v-for="link in links"><a :href="link.link">{{ link.text }}</a></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  props: {
    links: {
      type: Object,
      required: true
    },
  },
  data() {
    return {
      theme: "",
    }
  },
  computed() {
    if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
      toggleTheme();
    }
  },
  mounted() {
    let localTheme = localStorage.getItem('theme');
    document.documentElement.setAttribute('data-theme', localTheme);
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme == 'darkMode' ? '' : 'darkMode';
      document.documentElement.setAttribute('data-theme', this.theme);
      localStorage.setItem('theme', this.theme);
    }
  },
};
</script>

<style scoped>
nav {
  display: flex;
  justify-content: flex-end;
  position: relative;
  align-items: baseline;
  top: 0;
  right: 0;
  padding: 1rem 2rem;
  font-size: 1.125rem;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 1rem;
}

@media (max-width: 1024px) {
  nav {
    position: relative;
    padding: 5px 10px;
  }

  nav ul {
    display: none;
  }
}
</style>