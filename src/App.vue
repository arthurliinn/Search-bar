<template>
  <div id="app">
    <Search />
  </div>
</template>

<script>
import Search from './components/Search';

export default {
  name: 'App',
  components: {
    Search,
  },
};
</script>

<style>
  body{
    background: #83B5FF;
  }

  #app{
    position: fixed;

    top:50%;
    left:50%;

    transform: translate(-50% ,-50%);
  }
</style>
