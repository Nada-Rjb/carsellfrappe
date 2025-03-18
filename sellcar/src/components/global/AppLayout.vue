<template>
    <div class="layout"></div>
    <div>
      <AppNav></AppNav>
      <slot></slot>
      <main class="content"></main>
    </div>
  </template>
  <script>
  import AppNav from "./AppNav.vue";
  
  export default {
    data: () => ({}),
    components: {
      AppNav,
    },
  };
  </script>