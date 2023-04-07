<template>
      <NavBar :links="links" />
  <main>
      <Header :fullName="fullName" :logo="logo" />
    <Info />
  </main>
</template>

<script>
import Info from './components/Info.vue'
import Header from './components/Header.vue'
import NavBar from './components/NavBar.vue'

export default {
    name: "App",
    components: {
      Info,
      Header,
      NavBar
    },
    data() {
    return {
      fullName: "Huyen Nguyen",
      logo: "logo.png",
      links: [
        {
          text: "Education",
          link: "#education",
        },
        {
          text: "Work",
          link: "#work",
        },
        {
          text: "Projects",
          link: "#projects",
        },
        {
          text: "Contact",
          link: "#contact",
        },
      ],
    }
  },
};
</script>

<style scoped>
main {
  margin: 0 auto;
  max-width: 600px;
}

@media (min-width: 1024px) {
  main {
  max-width: 700px;
}

}
</style>