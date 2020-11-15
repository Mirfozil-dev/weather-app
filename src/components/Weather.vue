<template>
  <div v-if="typeof weather.main != 'undefined'" class="weather-wrapper">
    <div class="location-box">
      <div class="location">
        {{ weather.name }}, {{ weather.sys.country }}
      </div>
      <div class="date">
        {{ date }}
      </div>
    </div>
    <div class="weather-box">
      <div class="temp">{{ Math.round( weather.main.temp ) }}°C</div>
      <div class="weather">{{ weather.weather[0].main }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Weather",
  props: {
    weather: {
      type: Object,
      isRequired: true,
    },
    date: {
      type: String,
      isRequired: true,
    }
  }
}
</script>

<style scoped>

.weather-wrapper {
  margin-top: 100px;
}

.location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.date {
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
.weather-box {
  text-align: center;
}
.temp {
  display: inline-block;
  padding: 10px 25px;
  color: #ffffff;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather {
  color: #ffffff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);

}

</style>