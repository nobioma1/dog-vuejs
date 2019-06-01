<template>
  <div id="app">
    <Header/>
    <DogView
      v-bind:dog-breeds="dogBreeds"
      v-bind:current-breed="currentBreed"
      v-bind:dogImage="dogImage"
      v-bind:getDog="getDog"
      v-bind:randDog="randomDog"
      v-bind:isLoading="isLoading"
    />
  <Footer />
  </div>
</template>

<script>
import Header from './components/Header';
import DogView from './components/DogView';
import Footer from './components/Footer'

export default {
  name: "app",
  components: {
    Header,
    DogView,
    Footer
  },
  data() {
    return {
      dogBreeds: [],
      currentBreed: '',
      dogImage: '',
    };
  },
  methods: {
    fetchBreeds(URL) {
      fetch(URL)
        .then(res => {
          return res.json();
        })
        .then(data => (this.dogBreeds = Object.keys(data.message)))
        .catch(err => {
          throw new Error(err);
        });     
    },
    fetchImage(breed) {
      fetch(`https://dog.ceo/api/breed/${breed}/images/random`)
        .then(res => {
          return res.json();
        })
        .then(data => (this.dogImage = data.message))
        .catch(err => {
          this.dogImage = 'Sorry Can\'t load Image at the moment'
        }); 
    },
    getDog(e) {
      let value = e.target.value;
      if (value !== 'null') {
        this.currentBreed = value;
        this.fetchImage(value);
      }
    },
    randomDog() {
      let rand = Math.floor(Math.random() * this.dogBreeds.length);
      this.currentBreed = this.dogBreeds[rand];
      this.fetchImage(this.currentBreed);
    }
  },
  created() {
    const allDogsEndpoint = 'https://dog.ceo/api/breeds/list/all';
    this.fetchBreeds(allDogsEndpoint);
  }
};
</script>

<style>
*,
html {
  box-sizing: border-box;
}
</style>
