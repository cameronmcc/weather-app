<template>
  <div id="app">
    <main>
      <div class="title">
        <h1>To Get Started, Type a city and press Enter</h1>
      </div>
      <div class="search-box">
        <input
          type="text"
          name=""
          id=""
          class="search-bar"
          placeholder="Search..."
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>
      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }}, {{ weather.sys.country }}
          </div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>

        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main.temp) }}°f</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
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
        url_base: 'https://api.openweathermap.org/data/2.5/',
        query: '',
        weather: {},
      };
    },
    methods: {
      fetchWeather(e) {
        if (e.key == 'Enter') {
          fetch(
            `${this.url_base}weather?q=${this.query}&units=imperial&APPID=${this.api_key}`
          )
            .then((res) => {
              return res.json();
            })
            .then(this.setResults);
        }
      },
      setResults(results) {
        this.weather = results;
      },
      dateBuilder() {
        let d = new Date();
        let months = [
          'January',
          'February',
          'March',
          'April',
          'May',
          'June',
          'July',
          'August',
          'September',
          'October',
          'November',
          'December',
        ];
        let days = [
          'Sunday',
          'Monday',
          'Tuesday',
          'Wednesday',
          'Thursday',
          'Friday',
          'Saturday',
        ];
        let day = days[d.getDay()];
        let date = d.getDate();
        let month = months[d.getMonth()];
        let year = d.getFullYear();
        return `${day} ${date} ${month} ${year}`;
      },
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
    font-family: 'Mulish', sans-serif;
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

  .title {
    font-size: 5rem;
    text-align: center;
    margin: 1rem;
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
    color: rgb(0, 0, 0);
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

  .location-box .location {
    color: #fff;
    font-size: 3.5rem;
    font-weight: 500;
    text-align: center;
    text-shadow: 0.1rem 0.3rem rgba(0, 0, 0, 0.25);
  }

  .location-box .date {
    color: #fff;
    font-size: 2rem;
    font-weight: 300;
    font-style: italic;
    text-align: center;
  }

  .weather-box {
    text-align: center;
  }

  .weather-box .temp {
    display: inline-block;
    padding: 1rem 2.5rem;
    color: #fff;
    font-size: 10rem;
    font-weight: 900;
    text-shadow: 0.3rem 0.6rem rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.4);
    border-radius: 1.6rem;
    margin: 3rem 0;
    box-shadow: 0.2rem 0.4rem rgba(0, 0, 0, 0.25);
  }

  .weather-box .weather {
    color: #fff;
    font-size: 4rem;
    font-weight: 700;
    text-shadow: rgba(0, 0, 0, 0.25);
  }
</style>
