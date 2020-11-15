<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
    <main>
      <search-box v-model="query" />
      <weather :date="date" :weather="weather" />
    </main>
  </div>
</template>

<script>
import SearchBox from "@/components/SearchBox";
import Weather from "@/components/Weather";

export default {
  name: 'App',
  components: {
    SearchBox,
    Weather
  },
  data() {
    return {
      api_key: '8a81a2acf16b2a6cc7d0b66dc61b11ff',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  computed: {
    date(){
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    }
  },
  watch: {
    query: function (val) {
      fetch(`${this.url_base}weather?q=${val}&units=metric&APPID=${this.api_key}`).then(res => {
        return res.json();
      }).then(this.setResults);
    }
  },
  methods: {
    setResults(results) {
      this.weather = results
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  padding: 0;
  font-family: 'montserrat',sans-serif;
}
#app {
  width: 400px;
  background: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}
#app.warm {
  background: url("./assets/warm-bg.jpg");
  transition: 0.4s;
}

main{
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}
</style>
