<template>
  <nav role='navigation'>
    <label class="switch">
      <input type="checkbox" @change="toggleTheme()" :checked="this.theme == 'darkMode' ? true : false">
      <span class="slider">
        <IconMoon class="switch-icon" v-if="this.theme == 'darkMode'" />
        <IconSun class="switch-icon" v-else />
      </span>
    </label>

    <ul>
      <li v-for="link in links"><a :href="link.link">{{ link.text }}</a></li>
    </ul>
  </nav>
</template>

<script>
import IconMoon from './icons/IconMoon.vue';
import IconSun from './icons/IconSun.vue';

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
    };
  },
  mounted() {
    if (window.matchMedia && screen && window.matchMedia("(prefers-color-scheme: dark)").matches) {
      this.theme = "darkMode";
      document.documentElement.setAttribute("data-theme", "darkMode");
    }
    else {
      let localTheme = localStorage.getItem("theme");
      this.theme = localTheme;
      document.documentElement.setAttribute("data-theme", localTheme);
    }
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme == "darkMode" ? "" : "darkMode";
      document.documentElement.setAttribute("data-theme", this.theme);
      localStorage.setItem("theme", this.theme);
    }
  },
  components: { IconMoon, IconSun }
};
</script>

<style scoped>
.switch {
  position: relative;
  border-radius: 11px;
  display: block;
  width: 40px;
  height: 22px;
  flex-shrink: 0;
  border: 1px solid var(--color-border);
  background-color: var(--color-background-mute);
  transition: border-color .25s, background-color .25s;
  cursor: pointer;
}

.switch:hover {
  border-color: var(--color-border-hover);
}

.switch input {
  display: none;
}

.switch .slider {
  position: absolute;
  display: flex;
  place-items: center;
  place-content: center;
  top: 1px;
  left: 1px;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background-color: var(--color-background);
  box-shadow: var(--color-border-hover);
  transition: background-color .25s, transform .25s;
}

.switch input:checked+.slider {
  transform: translateX(18px);
}

.switch-icon {
  position: relative;
  width: 12px;
  height: 12px;
  fill: var(--color-heading);
}

nav {
  display: flex;
  justify-content: flex-end;
  position: relative;
  align-items: center;
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