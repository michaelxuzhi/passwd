<template>
    <ContainerPage />
</template>

<script>
import ContainerPage from './components/ContainerPage.vue';

export default {
    name: 'App',
    components: {
        ContainerPage,
    },
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
::-webkit-scrollbar {
    display: none;
}
</style>
