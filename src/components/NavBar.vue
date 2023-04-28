<template>
  <div id="modal" class="invisible">
          <div class="closebtn">
            <IconCross @click="toggleSettings()" />
          </div>
<div>
      <span>Switch Theme</span> <ThemeSwitch @toggleTheme="toggleTheme()" :theme="this.theme" />
</div>
<div>
  <span>Use user theme</span>
      <label class="switch" :class="{userActive: this.userChecked}">
    <input type="checkbox" @change="toggleUser()" :checked="this.userChecked" >
    <span class="slider">
    </span>
  </label>
</div>

  </div>
  <nav role='navigation'>
    <IconTheme id="theme-settings" @click="toggleSettings()" />
    <ul>
      <li v-for="link in links"><a :href="link.link">{{ link.text }}</a></li>
      <li>
        <ThemeSwitch @toggleTheme="toggleTheme()" :theme="this.theme"/>
      </li>
    </ul>

  </nav>
</template>

<script>
import ThemeSwitch from './ThemeSwitch.vue';
import IconMoon from './icons/IconMoon.vue';
import IconSun from './icons/IconSun.vue';
import IconTheme from './icons/IconTheme.vue';
import IconCross from './icons/IconCross.vue';

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
      userChecked: false,
    };
  },
  mounted() {
    let localTheme = localStorage.getItem("theme");
    if (localTheme == "userMode") {
      this.userChecked = true;
      if (window.matchMedia && screen && window.matchMedia("(prefers-color-scheme: dark)").matches) {
        this.theme = "darkMode";
        document.documentElement.setAttribute("data-theme", "darkMode");
      }
      else {
        this.theme = "lightMode";
        document.documentElement.setAttribute("data-theme", "lightMode");
      }
      return 0;
    }
      this.theme = localTheme;
      document.documentElement.setAttribute("data-theme", localTheme);
      return 0;
  },
  methods: {
    toggleTheme() {
      this.userChecked = false;
      this.theme = this.theme == "darkMode" ? "lightMode" : "darkMode";
      document.documentElement.setAttribute("data-theme", this.theme);
      localStorage.setItem("theme", this.theme);
    },
    toggleSettings() {
      let cl = document.getElementById("modal").classList;
      if (cl.contains("invisible")) {
        cl.remove("invisible");
      }
      else {
        cl.add("invisible");
      }
    },
    toggleUser() {
      this.userChecked = this.userChecked ? false : true;
      localStorage.setItem("theme", "userMode");
      if (window.matchMedia && screen && window.matchMedia("(prefers-color-scheme: dark)").matches) {
        document.documentElement.setAttribute("data-theme", "darkMode");
      }
      else {
        document.documentElement.setAttribute("data-theme", "lightMode");
      }
    }
  },
  components: { IconMoon, IconSun, IconTheme, ThemeSwitch, IconCross }
};
</script>

<style scoped>
.userActive {
  background-color: hsla(160, 100%, 37%, 1);;
}

#theme-settings {
  display: none;
}

nav {
  display: flex;
  justify-content: flex-end;
  position: relative;
  top: 0;
  right: 0;
  padding: 1rem 1rem;
  font-size: 1.125rem;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 1rem;
  align-items: center;
}

nav ul li:last-of-type {
  border-left: 1px solid var(--color-border);
}

.invisible {
  display: none;
}

#modal {
  background-color: var(--color-background);
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;
  padding: 2rem;
}

#modal div {
  display: flex;
  padding-bottom: 1rem;
  align-items: center;
}

.closebtn {
  justify-content: end;
}

.closebtn > * {
  width: 20px;
  height: 20px;
  cursor: pointer;
}

@media (max-width: 992px) {
  #theme-settings {
    display: block;
    cursor: pointer;
  }

  nav {
    position: relative;
    padding: 10px 10px;
  }

  nav ul {
    display: none;
  }
}
</style>