<template>
    <h1>{{ title }}</h1>
</template>

<script>
    export default {
        name: 'Header',
        props: {
            title: String
        }
    }
</script>

<style scoped>
 @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
    h1 {
        font-family: 'Roboto';
        font-weight: bold;
        font-size: 2.5em;

    }
</style>