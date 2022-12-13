<template>
  <v-container>
    <!-- <v-layout> -->
    <h1 class="display-1 text-xs-center">Weather App</h1>
    <v-col cols="12">
      <v-card color="blue" dark>
        <v-card-text>
          <v-layout v-if="weather.weather" justify-center>
            <!-- v if gunanya untuk meload data setelah data di wheather{} di isi -->
            <v-flex class="text-xs-center">
              <h4>Temperature</h4>
              <h1 class="display-1">{{ weather.name }}</h1>
              <h1 class="display-1">{{ temp() }} &deg;c</h1>
              <img :src="icon" alt="icon wheather" />
            </v-flex>
            <v-flex class="text-xs-center">
              <h4>Wind & Preasure</h4>
              <h3 class="headline">
                Wind: {{ weather.wind.speed }} m/s({{ weather.wind.deg }})&deg;
              </h3>
              <h3 class="headline mt-4">
                Preasure: {{ weather.main.preasure }}hPa
              </h3>
            </v-flex>
            <v-flex>
              <h4>Other:</h4>
              <h3 class="headline mt-4">
                Min Temperature:
                {{ Math.round(weather.main.temp_min - 273) }} &deg; C
              </h3>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col cols="12" class="mt-4">
      <v-form @submit.prevent="getWeatherInfo">
        <v-text-field label="Enter City Name" v-model="city"></v-text-field>
      </v-form>
    </v-col>
    <!-- </v-layout> -->
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: "London",
      weather: {},
    };
  },
  created() {
    this.getWeatherInfo();
  },
  computed: {
    icon() {
      return this.weather.weather
        ? `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png`
        : "";
      //membuat icon dinamis mengambil dari api JIKA icon yang akan di load
    },
  },
  // computed untuk mengambil dan membalikan api icon yang di atas
  methods: {
    getWeatherInfo() {
      this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=a1071eec5cfdeb650475b19c61911ebe`
        )
        .then((res) => (this.weather = res));
    },
    temp() {
      return this.weather.main ? Math.round(this.weather.main.temp - 273) : "";
    },
  },
};
</script>

<style></style>
