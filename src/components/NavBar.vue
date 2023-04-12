<template>
    <nav role='navigation'>
        <ul>
            <li v-for="link in links"><a :href="link.link">{{link.text}}</a></li>
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
    }
};
</script>

<style scoped>
nav {
    display: flex;
    justify-content: flex-end;
    position: sticky;
    top: 0;
    right: 0;
    padding: 1em 2em;
    font-size: 1.125rem;
}

nav ul {
    background: var(--color-background);
    list-style: none;
    display: flex;
    gap: 1rem;
    margin: 0;
    padding: 0;
}

nav ul li {
    flex-grow: 1;
    justify-content: space-evenly;
    min-width: 0;
}


@media (max-width: 1024px) {
    nav {
        display: none;
    }
  }
</style>