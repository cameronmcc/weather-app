<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input
          type="text"
          name=""
          id=""
          class="search-bar"
          placeholder="Search..."
        />
      </div>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        api_key: 'a31707b1786c4d3e65737234b5419521',
      };
    },
  };
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-size: 62.5%;
  }

  body {
    font-family: 'monsterrat', sans-serif;
  }

  #app {
    background-image: url('./assets/bg2.jpg');
    background-size: cover;
    background-position: bottom;
    transition: 0.4s;
  }

  main {
    min-height: 100vh;
    padding: 2.5rem;
    background-image: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.25),
      rgba(0, 0, 0, 0.75)
    );
  }
  .search-box {
  }
</style>
