<script>
    import AppHeader from './components/AppHeader.vue';
    import AppMain from './components/AppMain.vue';

    export default {
    name: "AppVue",
    components: {
      AppHeader,
      AppMain
    }
  }
</script>

<template>
    <AppHeader/>
    <AppMain/>
</template>

<style lang="scss">
  @use '../node_modules/bootstrap/scss/bootstrap.scss' as *;
  @use './styles/general.scss' as *;

</style>