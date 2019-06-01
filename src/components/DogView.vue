<template>
  <div class="dog-view-container">
    <h2>{{ currentBreed ? currentBreed.charAt(0).toUpperCase() + currentBreed.slice(1) : 'Good Doggy' }}</h2>
    <div class="dog-view">
      <div class="image-container">
        <img
          v-bind:src="currentBreed 
            ? dogImage 
            : require('../assets/good_doggy.svg')"
          alt="Dog image"
        >
      </div>
      <div class="buttons">
        <select @change="getDog">
          <option value="null">Select Dog Breed</option>
          <option v-for="breed in dogBreeds" v-bind:key="breed">{{ breed }}</option>
        </select>
        <button @click="randDog">Random</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DogView",
  props: ["dog-breeds", "current-breed", "dogImage", "getDog", "randDog"],
};
</script>

<style scoped>
.dog-view-container {
  margin: 0;
  margin-top: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.dog-view-container h2 {
  color: white;
  background-color: gray;
  width: 50%;
  text-align: center;
  margin: 0;
  padding: 10px;
}

.dog-view {
  position: relative;
  background-color: #c5d1eb;
  width: 50%;
  height: 60vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  box-shadow: 2px 6px 5px 0px rgba(191,187,191,1);
}

.dog-view .image-container {
  width: 100%;
  height: 100%;
}

.dog-view .image-container img {
  width: 100%;
  height: 100%;
}

.buttons {
  position: absolute;
  bottom: 5px;
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.buttons select,
.buttons button {
  font-size: 14px;
  padding: 10px;
  border: 1px solid gray;
  margin: 2px;
}

.buttons select:focus,
.buttons button:focus {
  outline: none;
}

.buttons select {
  width: 68%;
}

.buttons button {
  width: 28%;
  border-radius: 5px;
  background-color: grey;
  color: white;
}
.buttons button:hover {
  color: grey;
  background-color: white;
}

@media (max-width: 500px) {
  .dog-view,
  .dog-view-container h2 {
    width: 95%;
  }
}
</style>
