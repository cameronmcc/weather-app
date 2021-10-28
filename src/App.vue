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
      <div class="weather-wrap">
        <div class="location-box">
          <div class="location">Los Angeles</div>
          <div class="date">Thursday, October 20th 2021</div>
        </div>
        <div class="weather-box">
          <div class="temp">70°f</div>
          <div class="weather">Sunny</div>
        </div>
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
    color: #fff;
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

  .search-bar::placeholder {
    color: #fff;
  }
  .search-box {
    width: 100%;
    margin-bottom: 3rem;
  }
  .search-box .search-bar {
    display: block;
    width: 100%;
    padding: 3rem;
    color: #fff;
    font-size: 2rem;
    appearance: none;
    border: none;
    outline: none;
    background: none;
    background-color: rgba(255, 255, 255, 0.4);
    border-radius: 0.5rem;
    box-shadow: 0 0 0.8rem rgba(0, 0, 0, 0.25);
    transition: 0.4s;
  }

  .search-box .search-bar:focus {
    background-color: rgba(255, 255, 255, 0.6);
    box-shadow: 0 0 1.6rem rgba(0, 0, 0, 0.25);
  }

  .search-box .search-bar:hover {
    background-color: rgba(255, 255, 255, 0.6);
  }
</style>
