<template>
  <header>
    <div class="intro">
      <h1>
        <a href="/"><img alt="Logo" class="logo" :src="getImgUrl(logo)" /></a>
        {{ fullName }}
      </h1>
    </div>

  </header>
</template>

<script>
export default {
  name: "Header",
  methods: {
    getImgUrl(img) {
      return "src/assets/" + img;
    },
  },
  props: {
    fullName: {
      type: String,
      required: true
    },
    logo: {
      type: String,
      required: true
    },
  }
};
</script>

<style scoped>
.intro {
  line-height: 1.5;
}

h1 {
  font-weight: 500;
  color: var(--color-heading);
}

.logo {
  margin: 0 1rem 0 0;
  float: left;
  width: 32px;
  height: 32px;
  top: 5px;
}

@media (min-width: 1024px) {
  .intro {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: -0.6rem 0 1rem 0;
    top: calc(50% - 25px);
    left: -26px;
    width: 50px;
    height: 50px;
  }
}
</style>
