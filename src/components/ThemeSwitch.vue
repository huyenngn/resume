<template>
  <label class="switch">
    <input type="checkbox" @change="$emit('toggleTheme')" :checked="this.theme == 'darkMode' ? true : false">
    <span class="slider">
      <IconMoon class="switch-icon" v-if="this.theme == 'darkMode'" />
      <IconSun class="switch-icon" v-else />
    </span>
  </label>
</template>

<script>
import IconMoon from './icons/IconMoon.vue';
import IconSun from './icons/IconSun.vue';
import IconTheme from './icons/IconTheme.vue';

export default {
  name: "NavBar",
  props: {
    theme: {
      type: String,
      required: true
    },
  },
  data() {
    return {
    };
  },
  components: { IconMoon, IconSun, IconTheme }
};
</script>

<style scoped>
.switch-icon {
  position: relative;
  width: 12px;
  height: 12px;
  fill: var(--color-heading);
}
</style>